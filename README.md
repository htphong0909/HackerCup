# HackerCup2024_Practice A: Walk the Line
![image](https://hackmd.io/_uploads/HysWjCR6A.png)
## Tóm tắt
Cho $N$ người ở bên trái cầu, ta cần dẫn $N$ người này qua bên còn lại.

Để qua cầu ta cần đèn pin, và $N$ người chỉ có một cái đèn pin. Do đó, đèn pin sẽ được vận chuyển qua lại.

Mỗi lượt qua cầu chỉ được tối đa $2$ người qua cùng hướng, vậy có $2$ trường hợp qua cầu:
* Chỉ có người $i$ qua cầu: thời gian qua cầu là $S_i$
* Có cả người $i$ và $j$ cùng qua cầu: thời gian qua cầu là $\min(S_i, S_j)$.

In ra $YES$ nếu có cách đưa hết $N$ người qua cầu trong thời gian không quá $K$, ngược lại in ra $NO$.

## Ý tưởng

Gọi bên trái cầu là $A$, bên phải cầu là $B$.

Nhận thấy: ==nếu cả 2 người $i, j$ cùng qua cầu thì thời gian sẽ tốn $\min(S_i, S_j).$==

Vì vậy để tối ưu nhất:
* Từ $A$ sang $B$ ta sẽ luôn đi $2$ người.
* Từ $B$ sang lại $A$ để đưa đèn pin về $A$ ta sẽ luôn đi $1$ người.

$\Rightarrow$ Ta sẽ tốn: 
==$N - 1$== lượt từ $A \rightarrow B$ và ==$N - 2$== lượt từ $B \rightarrow A$.
>nếu cả 2 người $i, j$ cùng qua cầu thì thời gian sẽ tốn $\min(S_i, S_j)$.

$\Rightarrow$ Chính vì tính chất này, trong mọi lượt qua cầu, người qua cầu sẽ luôn bao gồm người có thời gian qua cầu $S$ bé nhất.

Do đó, thời gian qua cầu tối ưu nhất sẽ là:

\begin{equation} 
    \large \min_{\forall i} S_i \times (N \times 2 - 3) 
\end{equation} 

Song với trường hợp đặc biệt $N = 1$, ta sẽ xử lí riêng.  

Độ phức tạp thời gian $O(N)$
## Code
```cpp=
#include <bits/stdc++.h>
#define int long long
using namespace std;

int32_t main() {
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);
    int t;
    cin >> t;
    for (int tt = 1; tt <= t; tt++) {
        int n, k;
        cin >> n >> k;
        int minn = 1e18;
        for (int i = 1; i <= n; i++) {
            int x;
            cin >> x;
            minn = min(minn, x);
            //test
        }
        cout << (max(n * 2 - 3, 1LL) * minn <= k ? "YES" : "NO") << '\n';
    }
    return 0;
}
```
