## GPLT_Problem_Set

[TOC]



### L1-001 Hello World (5分)

这道超级简单的题目没有任何输入。
你只需要在一行中输出著名短句“Hello World!”就可以了。

#### 输入样例：

```c++
无
```

#### 输出样例：

```c++
Hello World!
```

#### My Solution:

```c++
#include <stdio.h>

int main(void)
{
    printf("Hello World!");

    return 0;
}
```



------



### L1-010 比较大小 (10分)

本题要求将输入的任意3个整数从小到大输出。

#### 输入格式:

输入在一行中给出3个整数，其间以空格分隔。

#### 输出格式:

在一行中将3个整数从小到大输出，其间以“->”相连。

#### 输入样例:

```c++
4 2 8
```

#### 输出样例:

```C++
2->4->8
```
#### My Solution:

```c++
#include <iostream>
using namespace std;

void InsertionSort(long long arr[], int len)
{
	long long key;
	
	for (int i = 1; i < len; i++) {
		key = arr[i];
		int j = i-1;
		while (arr[j] > key && j >= 0) {
			arr[j+1] = arr[j];
			j--;
		}
		arr[j+1] = key;
	}
}

int main(void)
{
	long long arr[3];
	
	cin >> arr[0] >> arr[1] >> arr[2];
	InsertionSort(arr, 3);
	cout << arr[0] << "->" << arr[1] << "->" << arr[2];
	
	
	return 0;
}
```



