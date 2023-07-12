## Print the longest common subsequence of the given string

```.cpp
#include <iostream>

using namespace std;

int main() {
  string str1 = "SHINCHAN";
  string str2 = "NOHARAAA";

  int m = str1.length();
  int n = str2.length();

  // Create a table to store the LCS values.
  int lcs[m + 1][n + 1];

  // Initialize the table.
  for (int i = 0; i <= m; i++) {
    for (int j = 0; j <= n; j++) {
      if (i == 0 || j == 0) {
        lcs[i][j] = 0;
      } else if (str1[i - 1] == str2[j - 1]) {
        lcs[i][j] = lcs[i - 1][j - 1] + 1;
      } else {
        lcs[i][j] = max(lcs[i - 1][j], lcs[i][j - 1]);
      }
    }
  }

  // Print the LCS.
  int i = m, j = n;
  string lcs_str = "";
  while (i > 0 && j > 0) {
    if (str1[i - 1] == str2[j - 1]) {
      lcs_str += str1[i - 1];
      i--;
      j--;
    } else if (lcs[i - 1][j] > lcs[i][j - 1]) {
      i--;
    } else {
      j--;
    }
  }

  cout << "The longest common subsequence is: " << lcs_str << endl;

  return 0;
}

```
