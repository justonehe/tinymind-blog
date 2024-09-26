---
title: C++中的set洛谷P1059
date: 2024-09-26T07:49:05.081Z
---

题意是去掉序列中的重复元素并重新排序输出。
可以用数组排序后用unique函数去掉重复的元素。但是这题用set更加简单：
set是一个红黑数，会对加入的元素自动排序；set会自动去重，本题只要熟悉一下set的用法即可。
```c++
#include<bits/stdc++.h>
using namespace std;
int n;
set<int> s;
int main(){
	cin>>n;
	while(n--){
		int tmp;
		cin>>tmp;
		s.insert(tmp);
	}
	cout<<s.size()<<endl;
	for(auto a:s){
		cout<<a<<' ';
	}
	return 0;
}
```
