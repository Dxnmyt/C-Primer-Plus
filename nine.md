```markdown
## 设计一个函数min(x, y)， 返回两个double类型值的较小值。 在一个简单 的驱动程序中测试该函数

```c
#include <stdio.h>

double min(double x, double y);

int main()
{
	printf("enter:");
	double x, y;
	scanf(" %lf %lf", &x, &y);
	min(x, y);
	printf("%lf", min(x, y));
	return 0;
}

double min(double x, double y)
{
	double a = (x > y) ? y : x;
	return a;
}
```

## 设计一个函数chline(ch, i, j)， 打印指定的字符j行i列。 在一个简单的驱 动程序中测试该函数。

```c
#include <stdio.h>

int chline(char ch, int x, int y); //行:x 列:y

int main()
{
	printf("enter:\n");
	chline('*', 3, 2);
	return 0;
}

int chline(char ch, int x, int y)
{
	for(int i = 1; i <= x; i++)
	{
		for(int j = 1; j <= y; j++)
		{
			printf("%c", ch);
		}
		printf("\n");
	}

	return 0;
}
```

## 两数的调和平均数这样计算： 先得到两数的倒数， 然后计算两个倒数 的平均值， 最后取计算结果的倒数。 编写一个函数， 接受两个double类型的 参数， 返回这两个参数的调和平均数。

```c
#include <stdio.h>

double average(double x, double y);

int main()
{
	printf("enter:\n");
	double sum = average(3.23, 2.16);
	printf("%lf", sum);
	return 0;
}

double average(double x, double y)
{
	x = 1 / x;
	y = 1 / y;
	double sum = x + y;
	sum = 1 / sum;
	return sum;
}
```

## 编写并测试一个函数larger_of()， 该函数把两个double类型变量的值替 换为较大的值。 例如， larger_of(x, y)会把x和y中较大的值重新赋给两个变 量

```c
#include <stdio.h>

double larger_of(double *x, double *y);

int main()
{
	printf("enter:\n");
	double x, y;
	scanf("%lf %lf", &x, &y);
	double max = larger_of(&x, &y);
	x = y = max;
	printf("%lf %lf", x, y);
	return 0;
}

double larger_of(double *x, double *y)
{
	double tem;
	if(*x > *y)
	{
		tem = *x;
	}
	else
	{
		tem = *y;
	}
	return tem;
}
```

## 编写并测试一个函数， 该函数以3个double变量的地址作为参数， 把最 小值放入第1个函数， 中间值放入第2个变量， 最大值放入第3个变量。

```c
#include <stdio.h>

void sort3Doubles(double *x, double *y, double *z);
void swap(double *a, double *b);

int main()
{
	printf("enter:\n");
	double x, y, z;
	scanf("%lf %lf %lf", &x, &y, &z);
	sort3Doubles(&x, &y, &z);
	printf("%.2lf %.2lf %.2lf\n", x, y, z);
	return 0;
}

void swap(double *a, double *b)
{
	double temp = *a;
	*a = *b;
	*b = temp;
}

void sort3Doubles(double *x, double *y, double *z)
{
	if (*x > *y)
		swap(x, y);
	if (*x > *z)
		swap(x, z);
	if (*y > *z)
		swap(y, z);
}
```

## 编写并测试Fibonacci()函数， 该函数用循环代替递归计算斐波那契 数

```c
#include <stdio.h>


int Fibonacci(int n) {
    if (n <= 0) {
        return 0;
    } else if (n == 1) {
        return 1;
    } else {
        int fib_sequence[n + 1];
        fib_sequence[0] = 0;
        fib_sequence[1] = 1;
        for (int i = 2; i <= n; i++) {
            fib_sequence[i] = fib_sequence[i - 1] + fib_sequence[i - 2];
        }
        return fib_sequence[n];
    }
}

int main() {
    int n;
    printf("Enter the number of Fibonacci terms you want to calculate (>= 0): ");
    if (scanf("%d", &n) == 1) {
        int result = Fibonacci(n);
        printf("The %dth Fibonacci number is: %d\n", n, result);
    } else {
        printf("Invalid input. Please enter an integer.\n");
    }
    return 0;
}
```



















































