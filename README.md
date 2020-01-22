## GPLT_Problem_Set

## 目录

* [L1-001 Hello World (5分)](#L1-001-Hello-World)
* [L1-002 打印沙漏(20分)](#L1-002-打印沙漏)
* [L1-010 比较大小 (10分)](#L1-010-比较大小)
* [L1-011 A-B (20分)](#L1-011-A减B)
* [L1-012 计算指数 (5分)](#L1-012-计算指数)
* [L1-020 帅到没朋友 (20分)](#L1-020-帅到没朋友)

## L1 001 Hello World

这道超级简单的题目没有任何输入。
你只需要在一行中输出著名短句“Hello World!”就可以了。

### 输入样例：

```in
无
```

### 输出样例：

```out
Hello World!
```

### My Solution:

```c++
#include <stdio.h>

int main(void)
{
    printf("Hello World!");

    return 0;
}
```



------


## L1 002 打印沙漏



本题要求你写个程序把给定的符号打印成沙漏的形状。例如给定17个“*”，要求按下列格式打印

```
*****
 ***
  *
 ***
*****
```

所谓“沙漏形状”，是指每行输出奇数个符号；各行符号中心对齐；相邻两行符号数差2；符号数先从大到小顺序递减到1，再从小到大顺序递增；首尾符号数相等。

给定任意N个符号，不一定能正好组成一个沙漏。要求打印出的沙漏能用掉尽可能多的符号。

### 输入格式:

输入在一行给出1个正整数N（≤1000）和一个符号，中间以空格分隔。

### 输出格式:

首先打印出由给定符号组成的最大的沙漏形状，最后在一行中输出剩下没用掉的符号数。

### 输入样例:

```in
19 *
```

### 输出样例:

```out
*****
 ***
  *
 ***
*****
2
```
### My Solution:

```c++
#include <cstdio>
#include <cmath>
#define MAXN 1005
using namespace std;

void print(int x, char ch)
{
	if (x == 1) {
		printf("%c\n", ch);
		return;
	}	
	for (int i = x; i >=1; i--) {
		for (int j = 1; j <= ((2*x-1) - (2*i-1)) / 2; j++) {
			printf(" ");
		}
		for (int j = 1; j <= 2*i-1; j++) {
			printf("%c", ch);
		}
		printf("\n");
	}
	for (int i = 2; i <= x; i++) {
		for (int j = 1; j <= ((2*x-1) - (2*i-1)) / 2; j++) {
			printf(" ");
		}
		for (int j = 1; j <= 2*i-1; j++) {
			printf("%c", ch);
		}
		printf("\n");
	}
}

int main(void)
{
	int n;
	int ch;
	int x;
	
	scanf("%d %c", &n, &ch);
	x = sqrt((n+1)/2.0);
	print(x, ch);
	printf("%d", n - (2*x*x - 1));
	
	return 0;
}
```



------



## L1 010 比较大小

本题要求将输入的任意3个整数从小到大输出。

### 输入格式:

输入在一行中给出3个整数，其间以空格分隔。

### 输出格式:

在一行中将3个整数从小到大输出，其间以“->”相连。

### 输入样例:

```in
4 2 8
```

### 输出样例:

```out
2->4->8
```
### My Solution:

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



------




## L1 011 A减B

本题要求你计算*A*−*B*。不过麻烦的是，*A*和*B*都是字符串 —— 即从字符串*A*中把字符串*B*所包含的字符全删掉，剩下的字符组成的就是字符串*A*−*B*。

### 输入格式：

输入在2行中先后给出字符串*A*和*B*。两字符串的长度都不超过104，并且保证每个字符串都是由可见的ASCII码和空白字符组成，最后以换行符结束。

### 输出格式：

在一行中打印出*A*−*B*的结果字符串。

### 输入样例：

```in
I love GPLT!  It's a fun game!
aeiou
```

## 输出样例：

```out
I lv GPLT!  It's  fn gm!
```
## My Solution:
```c++
#include <cstdio>
#include <cstring>
using namespace std;

void solve(char A[], char B[])
{
	int lenA = strlen(A);
	int lenB = strlen(B);
	
	for (int i = 0; i < lenB; i++) {
		for (int j = 0; j < lenA; j++) {
			if (A[j] == '\n') {
				continue;
			}
			if (A[j] == B[i]) {
				A[j] = '\n';
			}
		}
	}
	
	for (int i = 0; i < lenA; i++) {
		if (A[i] != '\n') {
			printf("%c", A[i]);
		}
	}
}

int main(void)
{
	char A[10005];
	char B[10005];
	
	scanf("%[^\n]%*c", A);
	scanf("%[^\n]%*c", B);
	solve(A, B);
	
	return 0;
}
```



------



## L1 012 计算指数

真的没骗你，这道才是简单题 —— 对任意给定的不超过 10 的正整数 *n*，要求你输出 *2^n*。不难吧？

### 输入格式：

输入在一行中给出一个不超过 10 的正整数 *n*。

### 输出格式：

在一行中按照格式 `2^n = 计算结果` 输出 *2^n* 的值。

### 输入样例：

```in
5
```

### 输出样例：

```out
2^5 = 32
```
### My Solution:
```c++
#include <cstdio>
#include <cmath>

int main(void)
{
	int n;
	
	scanf("%d", &n);
	printf("2^%d = %.lf", n, pow(2.0, n));
	
	
	return 0;
}
```



------



## L1 020 帅到没朋友

当芸芸众生忙着在朋友圈中发照片的时候，总有一些人因为太帅而没有朋友。本题就要求你找出那些帅到没有朋友的人。

### 输入格式：

输入第一行给出一个正整数`N`（≤100），是已知朋友圈的个数；随后`N`行，每行首先给出一个正整数`K`（≤1000），为朋友圈中的人数，然后列出一个朋友圈内的所有人——为方便起见，每人对应一个ID号，为5位数字（从00000到99999），ID间以空格分隔；之后给出一个正整数`M`（≤10000），为待查询的人数；随后一行中列出`M`个待查询的ID，以空格分隔。

注意：没有朋友的人可以是根本没安装“朋友圈”，也可以是只有自己一个人在朋友圈的人。虽然有个别自恋狂会自己把自己反复加进朋友圈，但题目保证所有`K`超过1的朋友圈里都至少有2个不同的人。

### 输出格式：

按输入的顺序输出那些帅到没朋友的人。ID间用1个空格分隔，行的首尾不得有多余空格。如果没有人太帅，则输出`No one is handsome`。

注意：同一个人可以被查询多次，但只输出一次。

### 输入样例1：

```in
3
3 11111 22222 55555
2 33333 44444
4 55555 66666 99999 77777
8
55555 44444 10000 88888 22222 11111 23333 88888
```

### 输出样例1：

```out
10000 88888 23333 
```

### 输入样例2：

```
3
3 11111 22222 55555
2 33333 44444
4 55555 66666 99999 77777
4
55555 44444 22222 11111
```

### 输出样例2：

```
No one is handsome
```

### My Solution(两个测试点没过):

| 测试点 | 结果         | 耗时   | 内存    |
| ------ | ------------ | ------ | ------- |
| 0      | 答案正确     | 3 ms   | 380 KB  |
| 1      | 答案正确     | 3 ms   | 296 KB  |
| 2      | **答案错误** | 2 ms   | 256 KB  |
| 3      | 答案正确     | 2 ms   | 296 KB  |
| 4      | **答案错误** | 152 ms | 1380 KB |

```c++
#include <cstdio> 
#include <cstring>
#define LEN 10 

/*
3
3 11111 22222 55555
2 33333 44444
4 55555 66666 99999 77777
8
55555 44444 10000 88888 22222 11111 23333 88888
*/

bool hasPrinted(char printed[][LEN], char *str, int n)
{
	for (int i = 0; i < n; i++) {
		if (strcmp(printed[i], str) == 0) {
			return true;
		}
	}
	
	return false;
}

void search(char circle[][1005][LEN], int KTable[], char searchTable[][LEN], int n, int m)
{
	char printed[n][LEN];
	int cnt = 0;
	
	//遍历searchTable[], 处理每一个查询 
	for (int i = 0; i < m; i++) {
		bool inCircle = false;
		
		//对每个查询, 先去判断是否存在只有一个人的朋友圈且这个人就是他 
		for (int j = 0; j < n; j++) {
			if (KTable[j] == 1 && strcmp(circle[j][0], searchTable[i]) == 0) {
				inCircle = true;
				if (hasPrinted(printed, searchTable[i], cnt) == false) {
					strcpy(printed[cnt], searchTable[i]);
					if (cnt == 0) {
						printf("%s", searchTable[i]);
					} 
					else {
						printf(" %s", searchTable[i]);
					}
					cnt++;
				}
			}
		}
		
		//如果没有第一种情况, 遍历所有朋友圈, 判断是否不在朋友圈中 
		if (inCircle == false) {
			for (int j = 0; j < n; j++) {
				
				//test-def
				//printf("\nj=%d n=%d\n", j, n);
				//test-end
				
				for (int k = 0; k < KTable[j]; k++) {
					if (strcmp(searchTable[i], circle[j][k]) == 0) {
						inCircle = true;
						break;
					}
				}
			}
			if (inCircle == false) {
				if (hasPrinted(printed, searchTable[i], cnt) == false) {
					strcpy(printed[cnt], searchTable[i]);
					if (cnt == 0) {
						printf("%s", searchTable[i]);
					} 
					else {
						printf(" %s", searchTable[i]);
					}
					cnt++;
					
				}
			}
		}
		
	}
	if (cnt == 0) {
		printf("No one is handsome");
	}
}

int main(void)
{
	int n;
	int m;
	int KTable[1005];
	char searchTable[10005][LEN]; 
	char circle[105][1005][LEN];
	
	scanf("%d", &n);
	for (int i = 0; i < n; i++) {
		scanf("%d", &KTable[i]);
		for (int j = 0; j < KTable[i]; j++) {
			scanf("%s", circle[i][j]);
		}
	}
	scanf("%d", &m);
	for (int i = 0; i < m; i++) {
		scanf("%s", searchTable[i]);
	}
	
	search(circle, KTable, searchTable, n, m);
	
	return 0;
 } 
```



------


