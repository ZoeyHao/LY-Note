# 200.岛屿数量
给你一个由 '1'（陆地）和 '0'（水）组成的的二维网格，请你计算网格中岛屿的数量。

岛屿总是被水包围，并且每座岛屿只能由水平方向和/或竖直方向上相邻的陆地连接形成。

此外，你可以假设该网格的四条边均被水包围。

[原题链接](https://leetcode-cn.com/problems/number-of-islands)

## 方法1---BFS
- 遍历矩阵，如果当前位置为「1」，结果 + 1 
- 对该位置进行 BFS 查询，并且把查询到的元素全都变为「0」。
```
class Solution {
    public int numIslands(char[][] grid) {
        int res=0;
        for(int i=0;i<grid.length;i++){
            for(int j=0;j<grid[i].length;j++){
                if(grid[i][j]=='0'){
                    continue;
                }else{
                    res++;
                    grid[i][j]=0;
                    bfs(i,j,grid);
                }
            }
            
        }
        return res;
    }
    public void bfs(int x,int y,char[][] grid){
        if(x>0 && grid[x-1][y]=='1'){
            grid[x-1][y]='0';
            bfs(x-1,y,grid);
        }
        if(x < grid.length-1 && grid[x+1][y]=='1'){
            grid[x+1][y]='0';
            bfs(x+1,y,grid);
        }
        if(y > 0 && grid[x][y-1]=='1'){
            grid[x][y-1]='0';
            bfs(x,y-1,grid);
        }
        if(y < grid[x].length-1 && grid[x][y+1]=='1'){
            grid[x][y+1]='0';
            bfs(x,y+1,grid);
        }
    }
}
```
