
## C 语言循环语句练习

### 1. `for` 循环第一个语句可以输入 `printf`，不一定是变量赋值，只执行一次

```c
#include <stdio.h>
int main(void)
{
  intnum = 0;
  for (printf("Keep entering numbers!\n"); num != 6;)
  scanf("%d", &num);
  printf("That's the one I want!\n");
  return 0;
}
```

该程序打印第 1 行的句子一次， 在用户输入 6 之前不断接受数字：
```
Keep entering numbers!
3 5 8 6 That's the one I want！
```

### 2. 通过循环得到 n 的次方

```c
for(i = 1; i <= p; i++)
pow *= n;
```

### 3. 编写一个程序， 创建一个包含 26 个元素的数组， 并在其中储存 26 个小写字母。 然后打印数组的所有内容。

```c
#include <stdio.h>

int main()
{
	char ch = 'A';
	for(int i = 0; i < 26; i++)
	{
		printf("%c", ch);
		printf("  ");
		ch ++;
	}
	return 0;
}
```

### 4. 使用嵌套循环， 按下面的格式打印字符：

```
$
$$
$$$
$$$$
$$$$$
```

```c
#include <stdio.h>

int main()
{
	//char ch = 'A';
	for(int i = 0; i < 5; i++)
	{
		for(int t = i; t>=0; t--)
		{
			printf("$");
		}
		printf("\n");
	}
	return 0;
}
```

### 5. 使用嵌套循环， 按下面的格式打印字母：

```
F
FE
FED
FEDC
FEDCB
FEDCBA
```

```c
#include <stdio.h>

int main()
{
	for(int i = 0; i < 6; i++)
	{
		char ch = 'F';
		for(int j = 0; j <= i; j++)
		{
			printf("%c", ch);
			ch--;
		}
		printf("\n");
	}
	return 0;
}
```

### 6. ****5. 编写一个程序， 提示用户输入大写字母。 使用嵌套循环以下面金字塔型的格式打印字母：

```
    A
   ABA
  ABCBA
 ABCDCBA
ABCDEDCBA
```

```c
#include <stdio.h>

int main() {
    printf("inter specific uppercase letters\n");
    char ch;
    scanf("%c", &ch);
    int num_rows = ch - 'A' + 1;

    for (int row = 0; row < num_rows; row++) {
        for (int space = 0; space < num_rows - 1 - row; space++) {
            printf(" ");
        }

        for (char letter = 'A'; letter <= 'A' + row; letter++) {
            printf("%c", letter);
        }

        for (char letter = 'A' + row - 1; letter >= 'A'; letter--) {
            printf("%c", letter);
        }

        printf("\n");
    }

    return 0;
}
```

### 7. 编写一个程序把一个单词读入一个字符数组中， 然后倒序打印这个单词。 提示： `strlen()` 函数（第 4 章介绍过） 可用于计算数组最后一个字符的下标

```c
#include <stdio.h>
#include <string.h>

int main()
{
	char word[50];
	printf("inter the word\n");
	scanf("%s", word); \\%s读取字符串
	int length = strlen(word);

	for(int i  = length - 1; i >= 0; i--)
	{
		printf("%c", word[i]);
	}
	return 0;
}
```

### 8. 10. 编写一个程序， 要求用户输入一个上限整数和一个下限整数， 计算从上限到下限范围内所有整数的平方和， 并显示计算结果。 然后程序继续提示用户输入上限和下限整数， 并显示结果， 直到用户输入的上限整数小于下限整数为止。

```c
#include <stdio.h>

int main()
{
	printf("Enter lower and upper integer limits:");
	int lower, upper;
	scanf("%d %d", &lower, &upper);
	int sum = 0;
	while(lower <= upper)
	{
		for(int i = lower; i <= upper; i++)
		{
			int square = i * i;
			sum += square;
		}
		printf("The sums of the squares from %d to %d is %d\n", lower * lower, upper * upper, sum);
		printf("Enter next set of limits:");
		scanf("%d %d", &lower, &upper);
	}
	printf("Done");
	return 0;
}
```

### 9. 12. 考虑下面两个无限序列：

```
1.0 + 1.0/2.0 + 1.0/3.0 + 1.0/4.0 + ...
1.0 - 1.0/2.0 + 1.0/3.0 - 1.0/4.0 + ...
```

编写一个程序计算这两个无限序列的总和， 直到到达某次数。 提示： 奇数个 -1 相乘得 -1， 偶数个 -1 相乘得 1。 让用户交互地输入指定的次数， 当用户输入 0 或负值时结束输入。 查看运行 100 项、 1000 项、 10000 项后的总和， 是否发现每个序列都收敛于某值？

```c
#include<stdio.h>

int main()
{
	printf("inter:");
	int count;
	scanf("%d", &count);
	double sum = 0;
	int n = 1;
	double sum1 = 0;
	int sign = 1;
	for(int i = 1; i <= count; i++, sign *= -1)
	{
		sum += (double)1 / n;
		sum1 += (double)1 * sign / n;
		n++;
	}
	printf("sum = %lf\n", sum);
	printf("sum = %lf\n", sum1);
	return 0;
}
```

### 10. 13. 编写一个程序， 创建一个包含 8 个元素的 `int` 类型数组， 分别把数组元素设置为 2 的前 8 次幂。 使用 `for` 循环设置数组元素的值， 使用 `do while` 循环显示数组元素的值。

```c
#include<stdio.h>

int main()
{
	int a[8];
	int b = 1;
	for(int i = 0; i < 8; i++)
	{
		a[i] = b;
		b *= 2;
	}

	int c = 0;

	do
	{
		printf("%d  ", a[c]);
		c++;
	}while(c <= 7);

	return 0;
}
```

### 11. 编写一个程序， 创建两个包含 8 个元素的 `double` 类型数组， 使用循环提示用户为第一个数组输入 8 个值。 第二个数组元素的值设置为第一个数组对应元素的累积之和。 例如， 第二个数组的第 4 个元素的值是第一个数组前 4 个元素之和， 第二个数组的第 5 个元素的值是第一个数组前 5 个元素之和（用嵌套循环可以完成， 但是利用第二个数组的第 5 个元素是第二个数组的第 4 个元素与第一个数组的第 5 个元素之和， 只用一个循环就能完成任务， 不需要使用嵌套循环）。 最后， 使用循环显示两个数组的内容， 第一个数组显示成一行， 第二个数组显示在第一个数组的下一行， 而且每个元素都与第一个数组各元素相对应。

```c
#include<stdio.h>

int main()
{
	printf("inter:");
	double a1[8];
	double a2[8];
	int sum = 0;
	for(int i = 0; i < 8; i++)
	{
		scanf("%lf", &a1[i]);
		sum += a1[i];
		a2[i] = sum;
	}

	for(int a = 0; a < 8; a++)
	{
		printf("%lf ", a1[a]);
	}

	printf("\n");

	for(int b = 0; b < 8; b++)
	{
		printf("%lf ", a2[b]);
	}
	return 0;
}
```

### 12. Chuckie Lucky 赢得了 100 万美元（税后）， 他把奖金存入年利率 8% 的账户。 在每年的最后一天， Chuckie 取出 10 万美元。 编写一个程序， 计算多少年后 Chuckie 会取完账户的钱？

```c
#include<stdio.h>

int main()
{
	float CHmoy = 100.0;
	int years = 0;
	while(CHmoy > 0)
	{
		CHmoy *= 1.08;
		CHmoy -= 10;
		years++;
	}
	printf("%d", years);
	return 0;
}
```

### 13. Rabnud 博士加入了一个社交圈。 起初他有 5 个朋友。 他注意到他的朋友数量以下面的方式增长。 第 1 周少了 1 个朋友， 剩下的朋友数量翻倍； 第 2 周少了 2 个朋友， 剩下的朋友数量翻倍。 一般而言， 第 N 周少了 N 个朋友， 剩下的朋友数量翻倍。 编写一个程序， 计算并显示 Rabnud 博士每周的朋友数量。 该程序一直运行， 直到超过邓巴数（Dunbar’s number）。 邓巴数是粗略估算一个人在社交圈中有稳定关系的成员的最大值， 该值大约是 150。

```c
#include<stdio.h>

#define Dunnum 150

int main()
{
	int fri = 5;
	for(int i = 1; fri < Dunnum; i++)
	{
		fri -= i;
		fri *= 2;
		printf("%d  ", fri);
	}

	return 0;
}
```
