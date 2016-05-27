# 动态规划&马尔科夫模型
<br>
## 动态规划
1. 先看一个例子

    给定一个m行n列的矩阵，矩阵每个元素是一个正整数，你现在在左上角（第一行第一列），你需要走到右下角（第m行，第n列），每次只能朝右或者下走到相邻的位置，不能走出矩阵。走过的数的总和作为你的得分，求最大的得分。

方式（1）
![](http://img.51nod.com/upload/000FBE97/08D24BF83D0592320000000000000009.png)

方式（2）
![](http://img.51nod.com/upload/000FBE98/08D24CCD942471F60000000000000002.png)

那么，我们不难发现
![](http://img.51nod.com/upload/000FBE98/08D24CD34C0AE9440000000000000003.png)

	结论：从起点到终点的最优路径上经过了(m + n – 1)个点，则这条路径上对应起点到这(m + n – 1)个点的子路径也都从起点到该位置的所有路径中和最大的路径。

状态转移图
![](http://img.51nod.com/upload/000FBE98/08D24CDA8D506CCC0000000000000006.png)

code：

    #include<bits/stdc++.h>
	using namespace std;

	int main()
	{
    	int a[510][510];
    	int n;
    	cin>>n;
    	for(int i=0;i<n;i++){
        	for(int j=0;j<n;j++){
        	    cin>>a[i][j];
       		}
    	}
    	for(int i=1;i<n;i++){
        	a[0][i] += a[0][i-1];
        	a[i][0] += a[i-1][0];
    	}
    	for(int i=1;i<n;i++){
        	for(int j=1;j<n;j++){
        	    a[i][j]=max(a[i-1][j],a[i][j-1])+a[i][j];
        	}
    	}
    	cout<<a[n-1][n-1]<<endl;
    	return 0;
	}

2.最大子段和


 
