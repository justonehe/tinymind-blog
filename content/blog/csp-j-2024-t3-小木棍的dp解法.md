---
title: CSP-J 2024 T3 小木棍的DP解法
date: 2024-11-06T14:14:04.761Z
---

本题的分类讨论有一种情况在考场上很难想到，根据题目中的特殊性质，容易想到对7取模之后枚举，但是17根木棍的最小情况不是488而是200，这个非常难发现。
如果用动态规划来做的话，就避免了分类讨论不完整的可能。
```cpp
#include <bits/stdc++.h>
using namespace std;
int a[10] = {6, 2, 5, 5, 4, 5, 6, 3, 7, 6};
int t, n, f[100005];
int main() {
	memset(f, 127, sizeof f);
	f[0] = 0;
	for (int i = 1; i <= 100000; i++)
		for (int j = 0; j < 10; j++)
			if (a[j] <= i)
				f[i] = min(f[i], f[i - a[j]] + 1);
	cin >> t;
	while (t--) {
		cin >> n;
		if (f[n] > 1 << 30) {
			cout << -1 << endl;
			continue;
		}
		int l = 1;
		while (n) {
			for (int j = l; j < 10; j++)
				if (a[j] <= n && f[n - a[j]] == f[n] - 1) {
					cout << j;
					n -= a[j];
					break;
				}
			l = 0;
		}
		cout << endl;
	}
	return 0;
}
```