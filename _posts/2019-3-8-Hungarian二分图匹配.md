---
published: true
title: Hungarian二分图匹配
category: Algorithm
tags: 
  - 二分图
layout: post
---


# 基本概念

## 二分图

是图论中的一种特殊模型。若能将无向图G=(V,E)的顶点V划分为两个交集为空的顶点集，并且任意边的两个端点都分属于两个集合，则称图G为一个为二分图。

![0](https://raw.githubusercontent.com/lyp22/lyp22.github.io/master/_posts/image/二分法/1.png)

## 匹配

一个匹配即一个包含若干条边的集合，且其中任意两条边没有公共端点。如下图，图3的红边即为图2的一个匹配。

![0](https://raw.githubusercontent.com/lyp22/lyp22.github.io/master/_posts/image/二分法/2.png)
![0](https://raw.githubusercontent.com/lyp22/lyp22.github.io/master/_posts/image/二分法/3.png)

## 最大匹配

在G的一个子图M中，M的边集中的任意两条边都不依附于同一个顶点，则称M是一个匹配。选择这样的边数最大的子集称为图的最大匹配问题,最大匹配的边数称为最大匹配数.如果一个匹配中，图中的每个顶点都和图中某条边相关联，则称此匹配为完全匹配，也称作完备匹配。如果在左右两边加上源汇点后，图G等价于一个网络流，最大匹配问题可以转为最大流的问题。解决此问的匈牙利算法的本质就是寻找最大流的增广路径。上图中的最大匹配如下图红边所示：

 

## 最优匹配

最优匹配又称为带权最大匹配，是指在带有权值边的二分图中，求一个匹配使得匹配边上的权值和最大。一般X和Y集合顶点个数相同，最优匹配也是一个完备匹配，即每个顶点都被匹配。如果个数不相等，可以通过补点加0边实现转化。一般使用KM算法解决该问题。

 

## 最小覆盖

二分图的最小覆盖分为最小顶点覆盖和最小路径覆盖：

①最小顶点覆盖是指最少的顶点数使得二分图G中的每条边都至少与其中一个点相关联，二分图的最小顶点覆盖数=二分图的最大匹配数；

②最小路径覆盖也称为最小边覆盖，是指用尽量少的不相交简单路径覆盖二分图中的所有顶点。二分图的最小路径覆盖数=|V|-二分图的最大匹配数；

 

## 最大独立集

最大独立集是指寻找一个点集，使得其中任意两点在图中无对应边。对于一般图来说，最大独立集是一个NP完全问题，对于二分图来说最大独立集=|V|-二分图的最大匹配数。如下图中黑色点即为一个最大独立集：

 

## 基本概念—匈牙利算法

交替路：从一个未匹配点出发，依次经过非匹配边、匹配边、非匹配边...形成的路径叫交替路。*

增广路：从一个未匹配点出发，走交替路，如果途径另一个未匹配点（出发的点不算），则这条交替路称为增广路（agumenting path）。

# 最大匹配与最小点覆盖

## 最小点覆盖
假如选了一个点就相当于覆盖了以它为端点的所有边，你需要选择最少的点来覆盖所有的边

## 最小割定理
是一个二分图中很重要的定理：一个二分图中的最大匹配数等于这个图中的最小点覆盖数。

 

## 最小点集覆盖==最大匹配
在这里解释一下原因，首先，最小点集覆盖一定>=最大匹配，因为假设最大匹配为n，那么我们就得到了n条互不相邻的边，光覆盖这些边就要用到n个点。现在我们来思考为什么最小点击覆盖一定<=最大匹配。任何一种n个点的最小点击覆盖，一定可以转化成一个n的最大匹配。因为最小点集覆盖中的每个点都能找到至少一条只有一个端点在点集中的边（如果找不到则说明该点所有的边的另外一个端点都被覆盖，所以该点则没必要被覆盖，和它在最小点集覆盖中相矛盾），只要每个端点都选择一个这样的边，就必然能转化为一个匹配数与点集覆盖的点数相等的匹配方案。所以最大匹配至少为最小点集覆盖数，即最小点击覆盖一定<=最大匹配。综上，二者相等。

# 匈牙利算法

由增广路的性质，增广路中的匹配边总是比未匹配边多一条，所以如果我们放弃一条增广路中的匹配边，选取未匹配边作为匹配边，则匹配的数量就会增加。匈牙利算法就是在不断寻找增广路，如果找不到增广路，就说明达到了最大匹配。

先给一个例子 
1、起始没有匹配 

![0](https://raw.githubusercontent.com/lyp22/lyp22.github.io/master/_posts/image/二分法/4.png)

2、选中第一个x点找第一跟连线 

![0](https://raw.githubusercontent.com/lyp22/lyp22.github.io/master/_posts/image/二分法/5.png)


3、选中第二个点找第二跟连线 

![0](https://raw.githubusercontent.com/lyp22/lyp22.github.io/master/_posts/image/二分法/6.png)


4、发现x3的第一条边x3y1已经被人占了，找出x3出发的的交错路径x3-y1-x1-y4，把交错路中已在匹配上的边x1y1从匹配中去掉，剩余的边x3y1 x1y4加到匹配中去 

![0](https://raw.githubusercontent.com/lyp22/lyp22.github.io/master/_posts/image/二分法/7.png)

![0](https://raw.githubusercontent.com/lyp22/lyp22.github.io/master/_posts/image/二分法/8.png)

![0](https://raw.githubusercontent.com/lyp22/lyp22.github.io/master/_posts/image/二分法/9.png)


5、同理加入x4,x5。 

匈牙利算法可以深度有限或者广度优先，刚才的示例是深度优先，即x3找y1,y1已经有匹配，则找交错路。若是广度优先，应为：x3找y1,y1有匹配，x3找y2。

# 算法模板(邻接表 & C++)

 

深度优先匈牙利算法代码：

```
#define maxn 10//表示x集合和y集合中顶点的最大个数！
 int nx,ny;//x集合和y集合中顶点的个数
 int edge[maxn][maxn];//edge[i][j]为1表示ij可以匹配
 int cx[maxn],cy[maxn];//用来记录x集合中匹配的y元素是哪个！
 int visited[maxn];//用来记录该顶点是否被访问过！
 int path(int u)
 {
     int v;
     for(v=0;v<ny;v++)
     {
         if(edge[u][v]&&!visited[v])
         {
             visited[v]=1;
            if(cy[v]==-1||path(cy[v]))//如果y集合中的v元素没有匹配或者是v已经匹配，但是从cy[v]中能够找到一条增广路
             {
                 cx[u]=v;
                 cy[v]=u;
                 return 1;
             }
         }
     }
     return 0;
 }
 int maxmatch()
 {
     int res=0;
     memset(cx,0xff,sizeof(cx));//初始值为-1表示两个集合中都没有匹配的元素！
     memset(cy,0xff,sizeof(cy));
     for(int i=0;i<=nx;i++)
     {
         if(cx[i]==-1)
         {
             memset(visited,0,sizeof(visitited));
             res+=path(i);
         }
     }
     return res;
 }
 ```