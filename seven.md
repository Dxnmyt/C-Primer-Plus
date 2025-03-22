```markdown
## 编写一个程序， 读取整数直到用户输入 0。 输入结束后， 程序应报告 用户输入的偶数（不包括 0） 个数、 这些偶数的平均值、 输入的奇数个数及 其奇数的平均值。

```c
#include <stdio.h>

int main()
{
	printf("inter:");
	int a;
	int b = 0;
	int c = 0;
	int d = 0;
	int e = 0;
	while(scanf("%d", &a) == 1 && a != 0)
	{
		if(a % 2 == 0)
		{
			b += a;
			d++;
		}
		else
		{
			c += a;
			e++;
		}
	}
	printf("%d %d\n", d, e);
	if (d > 0)
	{
		printf("%.2f ", (float)b / d);
	}
	else
	{
		printf("%.2f ", 0.00);
	}
	if (e > 0)
	{
		printf("%.2f\n", (float)c / e);
	}
	else
	{
		printf("%.2f\n", 0.00);
	}
	return 0;
}
```

## 编写一个程序， 提示用户输入一周工作的小时数， 然后打印工资总 额、 税金和净收入。 做如下假设：
## a.基本工资 = 1000美元/小时
## b.加班（超过40小时） = 1.5倍的时间
## c.税率： 前300美元为15%
## 续150美元为20%
## 余下的为25%
## 用#define定义符号常量。 不用在意是否符合当前的税法

```c
#include <stdio.h>

#define mon 1000
#define tax1 0.15
#define tax2 0.2
#define tax3 0.25

int main()
{
	float earn, hour, gross_earn, tax;
	printf("inter:");
	scanf("%f", &hour);
	if(hour <= 40)
	{
		gross_earn = mon * hour;
	}
	else
	{
		gross_earn = mon * (40 + (hour - 40) * 1.5);
	}
	earn = gross_earn;
	tax = 0;
	if (earn <= 300)
	{
		tax = earn * tax1;
	}
	else if (earn <= 450)
	{
		tax = 300 * tax1 + (earn - 300) * tax2;
	}
	else
	{
		tax = 300 * tax1 + 150 * tax2 + (earn - 450) * tax3;
	}
	earn = gross_earn - tax;
	printf("%.2f\n", earn);
	return 0;
}
```

## 8.修改练习7的假设a， 让程序可以给出一个供选择的工资等级菜单。 使 用switch完成工资等级选择。 运行程序后， 显示的菜单应该类似这样：
## *****************************************************************
## Enter the number corresponding to the desired pay rate or action:
## 1) $8.75/hr 2) $9.33/hr
## 3) $10.00/hr 4) $11.20/hr
## 5) quit
## *****************************************************************
## 如果选择 1～4 其中的一个数字， 程序应该询问用户工作的小时数。 程 序要通过循环运行， 除非用户输入 5。 如果输入 1～5 以外的数字， 程序应 提醒用户输入正确的选项， 然后再重复显示菜单提示用户输入。 使用#define 创建符号常量表示各工资等级和税率。

```c
#include <stdio.h>

#define rate1 8.75
#define rate2 9.33
#define rate3 10.00
#define rate4 11.20
#define ot_rate 1.5
#define tax1 0.15
#define tax2 0.20
#define tax3 0.25
#define threshold1 300
#define threshold2 450
#define base_hours 40

int main()
{
	float hour, gross_pay, tax, net_pay;
	int choice;

	printf("*****************************************************************\n");
	printf("Enter the number corresponding to the desired pay rate or action:\n");
	printf("1) $%.2f/hr 2) $%.2f/hr 3) $%.2f/hr 4) $%.2f/hr 5) quit\n", rate1, rate2, rate3, rate4);
	printf("*****************************************************************\n");

	while(scanf("%d", &choice) == 1 && choice != 5)
	{
		if(choice < 1 || choice > 5)
		{
			printf("Please enter the number corresponding to the desired pay rate or action:\n");
			printf("1) $%.2f/hr 2) $%.2f/hr 3) $%.2f/hr 4) $%.2f/hr 5) quit\n", rate1, rate2, rate3, rate4);
			continue;
		}
		else
		{
			printf("Enter hours worked this week:\n");
			if (scanf("%f", &hour) == 1)
			{
				if (hour <= base_hours)
				{
					switch(choice)
					{
						case 1:
							gross_pay = rate1 * hour;
						break;
						case 2:
							gross_pay = rate2 * hour;
						break;
						case 3:
							gross_pay = rate3 * hour;
						break;
						case 4:
							gross_pay = rate4 * hour;
						break;
					}
				}
				else
				{
					switch(choice)
					{
						case 1:
							gross_pay = rate1 * base_hours + rate1 * ot_rate * (hour - base_hours);
						break;
						case 2:
							gross_pay = rate2 * base_hours + rate2 * ot_rate * (hour - base_hours);
						break;
						case 3:
							gross_pay = rate3 * base_hours + rate3 * ot_rate * (hour - base_hours);
						break;
						case 4:
							gross_pay = rate4 * base_hours + rate4 * ot_rate * (hour - base_hours);
						break;
					}
				}

				tax = 0;
				if (gross_pay <= threshold1)
				{
					tax = gross_pay * tax1;
				}
				else if (gross_pay <= threshold2)
				{
					tax = threshold1 * tax1 + (gross_pay - threshold1) * tax2;
				}
				else
				{
					tax = threshold1 * tax1 + (threshold2 - threshold1) * tax2 + (gross_pay - threshold2) * tax3;
				}

				net_pay = gross_pay - tax;

				printf("Gross pay: $%.2f\n", gross_pay);
				printf("Taxes: $%.2f\n", tax);
				printf("Net pay: $%.2f\n", net_pay);
			}
			else
			{
				printf("Invalid input for hours.\n");
				// Clear the input buffer
				while (getchar() != '\n');
			}
		}
		printf("\n*****************************************************************\n");
		printf("Enter the number corresponding to the desired pay rate or action:\n");
		printf("1) $%.2f/hr 2) $%.2f/hr 3) $%.2f/hr 4) $%.2f/hr 5) quit\n", rate1, rate2, rate3, rate4);
		printf("*****************************************************************\n");
	}

	printf("Bye!\n");

	return 0;
}
```

## 编写一个程序， 只接受正整数输入， 然后显示所有小于或等于该数的 素数。

```c
#include <stdio.h>

int main()
{
	printf("enter:");
	int a;
	scanf("%d", &a);
	if(a < 0)
	{
		printf("error\n");
	}
	else
	{
		for(int i = 2; i <= a; i++)
		{
			int is = 1;
			for(int j = 2; j * j <= i; j++)
			{
				if(i % j == 0)
				{
					is = 0;
					break;
				}
			}
			if(is)
			{
				printf("%d ", i);
			}
		}
		printf("\n");
	}
	return 0;
}
```

##  邮购杂货店出售的洋蓟售价为 2.05 美元/磅， 甜菜售价为 1.15 美元/磅， 胡萝卜售价为 1.09美元/磅。 在添加运费之前， 100美元的订单有 5%的打折优惠。 少于或等于5磅的订单收取6.5美元的运费和包装费， 5磅～ 20磅的订单收取14美元的运费和包装费， 超过20磅的订单在14美元的基础上 每续重1磅增加0.5美元。 编写一个程序， 在循环中用switch语句实现用户输 入不同的字母时有不同的响应， 即输入a的响应是让用户输入洋蓟的磅数， b 是甜菜的磅数， c是胡萝卜的磅数， q 是退出订购。 程序要记录累计的重 量。 即， 如果用户输入 4 磅的甜菜， 然后输入 5磅的甜菜， 程序应报告9磅 的甜菜。 然后， 该程序要计算货物总价、 折扣（如果有的话） 、 运费和包装 费。 随后， 程序应显示所有的购买信息： 物品售价、 订购的重量（单位： 磅） 、 订购的蔬菜费用、 订单的总费用、 折扣（如果有的话） 、 运费和包装 费， 以及所有的费用总额。

```c
#include <stdio.h>

#define am 2.05
#define bm 1.15
#define cm 1.09
#define DISCOUNT_THRESHOLD 100.0
#define DISCOUNT_RATE 0.05
#define SHIPPING_FEE_TIER1 6.5
#define SHIPPING_FEE_TIER2 14.0
#define SHIPPING_WEIGHT_TIER1 5.0
#define SHIPPING_WEIGHT_TIER2 20.0
#define SHIPPING_RATE_OVER_20 0.5

int main()
{
	float totala = 0;
	float totalb = 0;
	float totalc = 0;
	float pounds1 = 0;
	float pounds2 = 0;
	float pounds3 = 0;
	float mon1, mon2, mon3;
	float total_weight;
	float total_before_discount;
	float discount = 0.0;
	float shipping_fee = 0.0;
	float final_total;
	char s;

	printf("enter:");
	while(scanf(" %c", &s) == 1 && s != 'q')
	{
		if(s != 'a' && s != 'b' && s != 'c')
		{
			printf("error,enter next:\n");
			continue;
		}
		else
		{
			switch(s)
			{
				case 'a':
					printf("enter you need:");
					if (scanf("%f", &pounds1) == 1)
					{
						totala += pounds1;
					}
					else
					{
						printf("Invalid input for pounds.\n");
						while (getchar() != '\n');
					}
				break;

				case 'b':
					printf("enter you need:");
					if (scanf("%f", &pounds2) == 1)
					{
						totalb += pounds2;
					}
					else
					{
						printf("Invalid input for pounds.\n");
						while (getchar() != '\n');
					}
				break;

				case 'c':
					printf("enter you need:");
					if (scanf("%f", &pounds3) == 1)
					{
						totalc += pounds3;
					}
					else
					{
						printf("Invalid input for pounds.\n");
						while (getchar() != '\n');
					}
				break;
			}
		}
		printf("enter next:");
	}

	total_weight = totala + totalb + totalc;
	mon1 = totala * am;
	mon2 = totalb * bm;
	mon3 = totalc * cm;

	total_before_discount = mon1 + mon2 + mon3;

	if(total_before_discount >= DISCOUNT_THRESHOLD)
	{
		discount = total_before_discount * DISCOUNT_RATE;
	}

	if(total_weight <= SHIPPING_WEIGHT_TIER1)
	{
		shipping_fee = SHIPPING_FEE_TIER1;
	}
	else if(total_weight <= SHIPPING_WEIGHT_TIER2)
	{
		shipping_fee = SHIPPING_FEE_TIER2;
	}
	else
	{
		shipping_fee = SHIPPING_FEE_TIER2 + (total_weight - SHIPPING_WEIGHT_TIER2) * SHIPPING_RATE_OVER_20;
	}

	final_total = total_before_discount - discount + shipping_fee;

	printf("\n********************* Order Summary *********************\n");
	printf("Item\t\tPrice/lb\tWeight(lbs)\tCost\n");
	printf("-------------------------------------------------------\n");
	printf("Artichokes\t$%.2f\t\t%.2f\t\t$%.2f\n", am, totala, mon1);
	printf("Beets\t\t$%.2f\t\t%.2f\t\t$%.2f\n", bm, totalb, mon2);
	printf("Carrots\t\t$%.2f\t\t%.2f\t\t$%.2f\n", cm, totalc, mon3);
	printf("-------------------------------------------------------\n");
	printf("Total cost of vegetables: $%.2f\n", total_before_discount);
	if (discount > 0)
	{
		printf("Discount (%.0f%%):        -$%.2f\n", DISCOUNT_RATE * 100, discount);
	}
	printf("Shipping and packaging:  $%.2f\n", shipping_fee);
	printf("-------------------------------------------------------\n");
	printf("Total amount due:       $%.2f\n", final_total);
	printf("*******************************************************\n");

	return 0;
}
```
