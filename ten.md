```markdown
## 编写一个程序， 初始化一个double类型的数组， 然后把该数组的内容 拷贝至3个其他数组中（在main()中声明这4个数组） 。 使用带数组表示法的 函数进行第1份拷贝。 使用带指针表示法和指针递增的函数进行第2份拷贝。 把目标数组名、 源数组名和待拷贝的元素个数作为前两个函数的参数。 第3 个函数以目标数组名、 源数组名和指向源数组最后一个元素后面的元素的指 针。

```c
#include <stdio.h>

double arr(double a[], double b[], int n);
double array(double a[], double b[], double *p);

// a是目标，b是源数组

int main()
{
	double a[5] = {1, 2, 3, 4, 5};
	double b[5];
	int n = 5;
	for(int i = 0; i < 5; i++)
	{
		b[i] = a[i];
		printf("  %lf", b[i]);
	}
	printf("\n");

	double *end;
	end = b + n;
	arr(b, a, n);
	array(b, a, end);
	return 0;
}

double arr(double a[], double b[], int n)
{
	double *p;
	p = a;
	for(int i = 0; i < n; i++)
	{
		*p++ = b[i];
		printf("  %lf", a[i]);
	}
	printf("\n");

}

double array(double a[], double b[], double *p)
{
	double *t;
	double *q;
	q = b;
	t = a;
	while(q < p)
	{
		*a = *q;
		a++;
		q++;
	}
	for(int i = 0; i < 5; i++)
	{
		printf("  %lf", a[i]);
	}
}
```

## 编写一个函数， 返回储存在int类型数组中的最大值， 并在一个简单的 程序中测试该函数。

```c
#include <stdio.h>

int arr(int *a, int i);

int main()
{
	printf("enter:");
	int i, t;
	scanf(" %d", &i);
	int a[i];
	for(int j = 0; j < i; j++)
	{
		printf("enter num:");
		scanf("%d", &a[j]);
	}

	arr(a, i);

	return 0;
}

int arr(int *a, int i)
{
	int b = a[0];
	int max;
	for(int j = 1; j < i; j++)
	{
		if(b > a[j])
		{
			max = b;
		}
		else
		{
			max = a[j];
		}
	}

	printf("%d", max);
}
```

## 编写一个函数， 返回储存在double类型数组中最大值和最小值的差 值， 并在一个简单的程序中测试该函数。

```c
#include <stdio.h>

double arr(double *a, int i);

int main()
{
	printf("enter:");
	int i, t;
	scanf(" %d", &i);
	double a[i];
	for(int j = 0; j < i; j++)
	{
		printf("enter num:");
		scanf("%lf", &a[j]);
	}

	arr(a, i);

	return 0;
}

double arr(double *a, int i)
{
	double b = a[0];
	double c = a[0];
	double max, min;
	for(int j = 1; j < i; j++)
	{
		if(b > a[j])
		{
			max = b;
			min = a[j];
		}
		else
		{
			max = a[j];
			min = b;
		}
	}
	printf("  %lf", max - min);
}
```

## 编写一个函数， 把double类型数组中的数据倒序排列， 并在一个简单 的程序中测试该函数

```c
#include <stdio.h>

double arr(double a[], double b[], int n);


int main()
{
	double a[5] = {1, 2, 3, 4, 5};
	double b[5];
	int n = 5;
	for(int i = 0; i < 5; i++)
	{
		b[i] = a[i];
		printf("  %lf", b[i]);
	}
	printf("\n");

	arr(b, a, n);
	return 0;
}

double arr(double a[], double b[], int n)
{
	double *p;
	p = a + n - 1;
	for(int i = n - 1; i >= 0; i--)
	{
		*p-- = b[i];
		printf("  %lf", a[i]);
	}
	printf("\n");

}
```

## 编写一个程序， 初始化一个double类型的二维数组， 使用编程练习2中 的一个拷贝函数把该数组中的数据拷贝至另一个二维数组中（因为二维数组 是数组的数组， 所以可以使用处理一维数组的拷贝函数来处理数组中的每个 子数组） 。

```c
#include <stdio.h>

void arr(double b[][3], double a[][3], int n, int m);

int main() {
    double a[2][3] = {
        {1.53, 1.64, 1.38},
        {2.79, 2.56, 2.16}
    };
    double b[2][3];
    int n = 2;
    int m = 3;
    arr(b, a, n, m);
    return 0;
}

void arr(double b[][3], double a[][3], int n, int m) {
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < m; j++) {
            b[i][j] = a[i][j];
            printf("%lf ", b[i][j]);
        }
        printf("\n");
    }
}
```

## 方法二：AI给出指针方法

```c
#include <stdio.h>

void arr(double (*b)[3], double (*a)[3], int n, int m);

int main() {
    double a[2][3] = {
        {1.53, 1.64, 1.38},
        {2.79, 2.56, 2.16}
    };
    double b[2][3];
    int n = 2;  // 行数
    int m = 3;  // 列数
    arr(b, a, n, m);
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < m; j++) {
            printf("%lf ", b[i][j]);
        }
        printf("\n");
    }
    return 0;
}

void arr(double (*b)[3], double (*a)[3], int n, int m) {
    for(int i = 0; i < n; i++) {
        double *p_b = b[i];  // 指向目标数组的第 i 行
        double *p_a = a[i];  // 指向源数组的第 i 行
        for(int j = 0; j < m; j++) {
            *(p_b + j) = *(p_a + j);  // 使用指针偏移拷贝每个元素
        }
    }
}
```

## 编写一个程序， 提示用户输入3组数， 每组数包含5个double类型的数 （假设用户都正确地响应， 不会输入非数值数据） 。 该程序应完成下列任务。
## a.把用户输入的数据储存在3×5的数组中
## b.计算每组（5个） 数据的平均值
## c.计算所有数据的平均值
## d.找出这15个数据中的最大值
## e.打印结果
## 每个任务都要用单独的函数来完成（使用传统C处理数组的方式） 。 完 成任务b， 要编写一个计算并返回一维数组平均值的函数， 利用循环调用该 函数3次。 对于处理其他任务的函数， 应该把整个数组作为参数， 完成任务c 和d的函数应把结果返回主调函数。

```c
#include <stdio.h>

double average(double a[][5], int i, int j);
double find_max(double a[][5], int rows, int cols);

int main()
{
	int i, j;
	int n = 3;
	int m = 5;
	double k;
	printf("enter:\n");
	double a[3][5];
	for(i = 0; i < 3; i++)
	{
		for(j = 0; j < 5; j++)
		{
			scanf(" %lf", &a[i][j]);
			printf("  %lf", a[i][j]);
		}
		average(a, n, m);
		printf("\n");
	}
	k = average(a, n, m);
	printf("  %lf", k);
	double max_val = find_max(a, n, m);
	printf("\nMaximum value: %.2f\n", max_val);
	return 0;
}

double average(double a[][5], int i, int j)
{
	double sum = 0;
	double sum1 = 0;
	for(int n = 0; n < i; n++)
	{
		sum = 0;
		for(int t = 0; t < j; t++)
		{
			sum += a[n][t];
		}
		sum1 += sum;
		printf("  %lf", sum / 5);
	}
	sum1 /= i * j;
	return sum1;
}

double find_max(double a[][5], int rows, int cols)
{
	double max_val = a[0][0];
	for (int i = 0; i < rows; i++) {
		for (int j = 0; j < cols; j++) {
			if (a[i][j] > max_val) {
				max_val = a[i][j];
			}
		}
	}
	return max_val;
}
```


































