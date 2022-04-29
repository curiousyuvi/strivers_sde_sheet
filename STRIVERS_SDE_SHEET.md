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
  
- **Pascal's Triangle** :
  - **1st type** : Print the element on `rth` row and `cth` column 
    - print  <sup>(r-1)</sup> C <sub>(c-1)</sub>
  
  - **2nd type** : Print the whole triangle till `rth` row
    - create a `vector<vector<int>>` and every time push a new vector with 1st and last element as 1, and middle elemnts as pair sum of previous vector
    <details>
    <summary>Code :</summary>
    <br>
  
  
    ```c++
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> pt;
        pt.push_back(vector<int>());
        pt[0].push_back(1);
        
        if(numRows==1){
            return pt;
        }else{
            pt.push_back(vector<int>());
            pt[1].push_back(1);
            pt[1].push_back(1);
            
            for(int i=3;i<=numRows;i++){
                pt.push_back(vector<int>());
                pt[i-1].push_back(1);
                
                for(auto it=pt[i-2].begin();it!=(pt[i-2].end()-1);it++){
                    int sum = *it + *(it+1);
                    pt[i-1].push_back(sum);
                }
                
                pt[i-1].push_back(1);
            }
            
            return pt;
        }
      }
    ```
  </details>
      
  - **3rd type**: Print the rth row
      - here we will use nCr approach but smartly, we know we can calculate rC1 = rC0 * r / 1
      <details>
      <summary>Code :</summary>
      <br>
  
  
      ```c++
      vector<int> getRow(int rowIndex) {
        vector<int> temp={1};
        for(int i=1;i<=rowIndex;i++){
           long long newTerm = (((long long)temp.back())*((long long)(rowIndex-i+1)))/i;
           temp.push_back(newTerm);
        }
        
        return temp;
        
      }
      ```
    </details>

- **Next Permutaion** :
        - find the first element from last that holds `arr[i] < arr[i+1]`, take its index in k
        - then, find the first element from last that is `arr[i] > arr[k]`, call it j (do this only if k exists)
        - then, swap `arr[k]` and `arr[j]` do this only if `k!=-1` or k exists)
        - then, reverse all the elemnts in the right of `k` (do this only if k exists, else reverse whole arr)
        <details>
        <summary>Code :</summary>
        <br>
  
  
        ```c++
        void nextPermutation(vector<int>& nums) {
          int n=nums.size();
        
          int k=-1;
        
          for(int i=n-2;i>=0;i--){
            if(nums[i]<nums[i+1])
            {
                k=i;
                break;
            }
          }
        
        
        
          if(k!=-1){
            int j=-1;
            
            for(int i=n-1;i>=k;i--){
                if(nums[i]>nums[k])
                {
                    j=i;
                    break;
                }
            }
            
            swap(nums[k],nums[j]);
            reverse(nums.begin()+k+1,nums.end());
            
          }
          else{
              reverse(nums.begin(),nums.end());
          }
        
        }
        ```
        </details>
        
