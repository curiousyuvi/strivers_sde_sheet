# strivers_sde_sheet

## Day 1 : Arrays

- **Set Matrix Zeroes**
  - change the value of elemts to -1 instead of 0
  - use first row and first column to hash which row and column are zero
  - Code :
  ```c++
  void solve()
  {
    int i, j, n, m;
    cin >> n >> m;
    ll arr[n][m];

    fo(i, n)
    {
        fo(j, m)
        {
            cin >>
                arr[i][j];
            if (arr[i][j] == 0)
            {
                arr[0][j] = -1;
                arr[i][0] = -1;
            }
        }
    }

    fo(i, n)
    {
        fo(j, m)
        {
            if (arr[0][j] == -1 || arr[i][0] == -1)
                cout << 0 << " ";
            else
                cout << arr[i][j] << " ";
        }
        cout << endl;
    }
  }
  ```
