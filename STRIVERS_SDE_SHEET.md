# strivers_sde_sheet

## Day 1 : Arrays

- **Set Matrix Zeroes**
  - use first row and first column to represent which row and column are zero
  - since `matrix[0][0]` represents both firstRow and firstCol, you have to make `matrix[0][0]` only represent firstRow as 0, and some other flag bool represent firstCol as 0.
  <details>
  <summary>Code :</summary>
  <br>
  
  
  ```c++
  void setZeroes(vector<vector<int>>& matrix) {
        int n=matrix.size();
        int m=matrix[0].size();
        
        bool col=1;
        
        
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                
                if(matrix[i][j]==0){
                    if(j==0){
                        col=0;
                    }else{
                        matrix[0][j]=0;
                        matrix[i][0]=0;
                    }
                    
                }
            }
            
        }
        
        
        for(int i=n-1;i>=0;i--){
            for(int j=m-1;j>0;j--){
                
                if(matrix[i][0]==0)
                    matrix[i][j]=0;
                
                if(matrix[0][j]==0)
                    matrix[i][j]=0;
            }
        }
        
        
        if(!col){
            for(int i=0;i<n;i++)
              matrix[i][0]=0;
        }
        
   }
  ```
  </details>
