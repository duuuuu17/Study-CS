# Data Struct

## First：链表

### 链表的结构体

```c++
#define elemtype int;
typedef struct link_table{
    elemtype data;
    link_table * next;
}link_table, *head
```

### 初始化

```
void init_lt(head &L){//该初始化会构建一个头结点
	L = new linktable;
    L->next = NULL;
}
```

### 链表元素的插入

因为是链表所以会使用指针

先声明一个新节点 ,并返回该新节点地址
```c++
link_table *n= new link_table; 
```
#### 前插法:

```c++
head; //链表的头结点地址
n->next = head->next;//先将新节点的后继赋为原链表的首元结点
head->next = head//将新结点移至头结点后，称为新的首元结点
```



#### 尾插法：

```C++
tail; //链表的尾结点地址
tail->next = n->next;//先将新节点的前驱赋为原链表的尾结点
n->next = ^//将新结点的后继变为尾结点，即为空^
```

### 树

##### 二叉树层序遍历

使用两个队列，一个为存子树地址队列node_q，一个是存储子树值的队列data_q，根据data_q是否为空，来决定是否停止循环，其循环体为，根据node_q的左右子树是否为空，来选择入队其子树地址（是为了访问它的下一个子结点）和值（是为了访问它下一个子结点时，进行输出它的值)。

```c++
//层序遍历，利用后序遍历将同层元素压栈
void  push_layer_LRD(BTS_root root) {
	queue<BTS_root> node;//创建存储树节点地址的队列
	queue<int> q;//创建存储树节点值的队列
	if (root == NULL) return;
	q.push(root->data);//将根结点地址入队
	node.push(root);//将根结点值入队
	while (!q.empty()) {
		//当前存储指针队列的头结点的左孩子和右孩子，若不为空，则存储其child的值和地址
		if (node.front()->left != NULL) {
			q.push(node.front()->left->data);
			node.push(node.front()->left);
		}
		if (node.front()->right != NULL) {
			q.push(node.front()->right->data);
			node.push(node.front()->right);
		}
		cout << q.front() << endl;
		q.pop();//将根结点值出队
		node.pop();//将根结点地址出队

	}
}
```

## 图



### 图的遍历

无向图和有向图的区别在于构建的是邻接矩阵还是邻接表

邻接矩阵

$$
(G,E) =\left[ \begin{array}{ccc} 
1 &2 &3\\
2 \\
3
\end{array} \right] 以G_v顶点为下标的邻接矩阵，若顶点间有邻边，则其元素为1
$$

邻接表

$$
(G,E)=
\left[\begin{array}{c}
1\\
2\\
3\\
\vdots\\
n
\end{array}
\right]
\begin{array}{c}
\rightarrow\\
\rightarrow\\
\rightarrow\\
\rightarrow\\
\rightarrow
\end{array}
\begin{array}{c}
[2,3,4\ldots]\\
[3,1\ldots]\\
[6\ldots]\\ 
\vdots\\
[n\ldots]
\end{array}
即邻接表是二维的matrix_{n\times n},它的下标就为对应的顶点，而它所属的一维的sub\\_ martix_{1\times n},保存邻居顶点
$$

#### 深度优先DFS:

即从某一节点，访问邻居顶点，（已访问的顶点无法被访问，即无法重复进入顶点序列）然后根据邻居顶点再访问下一顶点，当无可访问邻居顶点时，返回至这一深度遍历顶点序列的初始顶点，然后访问其下一个邻居，依次反复，直至所有顶点被包含就停止。、

```python
#无向图构建深度遍历
def DFS_graph(self,start_node):
    #遍历时已到达该节点，故其被标注不可访问
    self.vertex_list[start_node] = False
    #复制邻接矩阵
    adj_matrix = self.adj_matrix
    for i in range(len(adj_matrix[start_node])):
        if adj_matrix[start_node][i] != 0 and self.vertex_list[i] == True:
            self.path.append(i + 1)
            self.DFS_graph(i)
```

```python
# 有向图的深度遍历
def DFS_digraph(self,start_node):
    #遍历时已到达该节点，故其被标注不可访问
    self.vertex_list[start_node] = False
    #复制邻接表
    adj_table = self.adj_table
    for i in range(len(adj_table[start_node])):
        if  adj_table[start_node][i] != 0 and self.vertex_list[ adj_table[start_node][i] -1 ] == True:
            self.path.append(adj_table[start_node][i])
            self.DFS_digraph(adj_table[start_node][i]-1)
```

#### 广度优先BFS：

类似于树的层次遍历，利用一个顶点是否可访问的列表，从而控制输出顶点访问序列。由于是广度的，所以它是类似于层次性输出。

```python
#无向图构建广度遍历
def BFS_graph(self,start_node):
    adj_matrix = self.adj_matrix
    self.vertex_list[start_node] = False
    for j in range(len(adj_matrix)):
        for i in range(len(adj_matrix[j])):
            if adj_matrix[j][i] != 0 and self.vertex_list[i] == True:
                self.path.append(i + 1)
                self.vertex_list[i] = False
```

```python
#有向图广度遍历
def BFS_digraph(self,start_node):
    adj_table = self.adj_table
    self.vertex_list[start_node] = False
    for j in range(len(adj_table)):
        for i in range(len(adj_table[j])):
            if adj_table[j][i] != 0 and self.vertex_list[ adj_table[j][i] -1] == True:
                self.path.append(adj_table[j][i])
                self.vertex_list[adj_table[j][i] -1 ] = False
```

