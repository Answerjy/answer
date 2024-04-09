###T组数据

```C
int T;
scanf("%d",&T);
while(T--){
    

}
```

#### 处理到文件结尾

```c
int n;
while(scanf("%d",&n)!=EOF){
    
    
}
```

#### 每组数据之间留空行

##### T组数据

数据后+换行符，最后一组数据不加换行符

```c
处理数据

if(T!=0){
    printf("\n");
}
```

##### 处理到文件结尾

数据前+换行符，第一组数据不加换行符

```c
int flag = 1;
while(T--){
    if(!flag){
        printf("\n");
    }
    else{
        flag = 0;
    }
  处理数据  
}
```

# 字符串遍历数字

```c
int count = 0;//记录数字出现个数
char str[80];//定义字符数组
scanf("%s", str);//输入字符串不用取地址符号
for (int i = 0;str[i] != '\0';i++) {//遍历字符串数组到结尾
	if ((int)str[i] >= 48 && (int)str[i] <= 57) {//强制转换类型查询ASC表
		count++;
	}
}
printf("%d\n", count);
```

# ==辗转相除法求最大公约数==

```c
int GCD(int m,int n){
    while(n!=0){
        int temp = m%n;
        m = n;
        n = temp;      
    }
    return m;//最后m和n会互换位置，所以是m为最大公约数
}
```

==最小公倍数为a*b/最大公约数==

# 空杯交换

```c
if(a<b){
    int temp = 0;
    temp =a;
    a = b;
    b = temp;  
}
```

# 判断素数

```c
#include <math.h>
int prime_num(int num){
    if(num<2){
        return 0;
    }
        for(int i =2;i<=sqrt(num);i++){//sqrt(开方函数,用math库)
            if(num%i==0){
                return 0;  
            }  
        }
    return 1;
}
```

# ==数字回文==

```c
int huiwen(int n){
    int temp = n;
    int reserve = 0;
    while(temp>0){
        reserve = reserve*10+temp%10;
        temp/=10;
    }
    return reserve;
}
```

# 三位数水仙花数

```c
int shui(int n){
    int c = n%10;
    int b = (n/10)%10;
    int a = n/100;
    if(c*c*c+b*b*b+c*c*c==n){
        return 1;    
    }
    else{
        return 0;
    }
}
```

# 二分查找

```c
int arr[]={1,2,3,4,5,6,7,8,9,10};
int k = 7;//查找元素
int sz = sizeof(arr)/sizeof(arr[0]);
int flag = 0;
int left = 0;
int right = sz-1;
while(left<=right){
    int mid = (left + right)/2;
    if(arr[mid]<k){
        left = mid+1;
    }
    else if(arr[mid]>k){
        right = mid-1;
    }
    else{
        flag = 1;
		printf("找到了，下标是%d\n", mid);
		break;
    }
}
if(flag==0){
    printf("没找到");
}

```

#####平均值计算

<img src="C:\Users\35132\AppData\Roaming\Typora\typora-user-images\image-20240311193416687.png" alt="image-20240311193416687" style="zoom: 33%;" />

# 百钱百鸡

<img src="C:\Users\35132\AppData\Roaming\Typora\typora-user-images\image-20240313172917395.png" alt="image-20240313172917395" style="zoom: 67%;" />

```c
#include <stdio.h>
int main() {
	int n;
	while (scanf("%d", &n) != EOF) {
		for (int i = 0; i <= 200; i++) {//题目中说n最多是1000，所以最多买200只公鸡
			for (int j = 0; j <= 333; j++) {//同理，最多买333只母鸡
				int k = n - i - j;
				if (k >= 0 && 5 * i + 3 * j + k / 3 == n && k % 3 == 0) {//三个条件缺一不可
					printf("%d %d %d\n", i, j, k);
				}
			}
		}
	}
	return 0;
}
```

#数据中间有空格，最后一个数据没有空格

##### 三七二十一

```c
#include <stdio.h>
int main() {
	int T;
	scanf("%d", &T);
	while (T--) {
		int a, b;
		scanf("%d %d", &a, &b);
		int flag = 0;//定义一个标志
		for (int i = a; i <= b; i++) {
			if (i % 3 == 2 && i % 7 == 1) {//如果满足
				if (flag != 0) {//第一个数据前没有空格
					printf(" ");
				}
				printf("%d", i);
				flag = 1;//改变flag，使除去第一个后面一致
			}
		}
		if (flag == 0) {
			printf("none\n");
		}
		else {
			printf("\n");
		}
	}
	return 0;
}
```

# 购物

<img src="C:\Users\35132\AppData\Roaming\Typora\typora-user-images\image-20240313202134488.png" alt="image-20240313202134488" style="zoom: 67%;" />

```c
#include <stdio.h>
#include <string.h>
int main() {
	int n;
	while (scanf("%d", &n) != EOF) {
		getchar(); // 消耗换行符
		char str[101][11]; // 假设字符串长度不超过10
		double arr[100];
		double max = 0.0;
		char max_str[11]; // 假设字符串长度不超过10
		double sum = 0.0;
		for (int i = 0; i < n; i++) {
			scanf("%10s", str[i]); // 读取字符串，限制长度为10
			getchar(); // 消耗空格或换行符
			scanf("%lf", &arr[i]);
			sum += arr[i];
			if (arr[i] > max) {
				max = arr[i];
				strcpy(max_str, str[i]); // 现在可以正确复制字符串了
			}
		}
		double avg = sum / n;
		printf("%s %.1lf\n", max_str, avg); // 打印字符串和平均值，格式化输出平均值
	}
	return 0;
}
```

字符串可以判断是否相等，但不能赋值

==赋值要用strcpy函数==

# 冒泡排序

```c
#include <stdio.h>
int main() {
    int n;
    while (scanf("%d", &n) != EOF) {
        int arr[100];
        for (int i = 0; i < n; i++) {//输入整形数组
            scanf("%d", &arr[i]);
        }
        for (int i = 0; i < n - 1; i++) {//冒泡排序
            for (int j = 0; j < n - 1 - i; j++) {
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
        for (int i = 0; i < n; i++) {//输出排序后数组
            printf("%d", arr[i]);
            if (i < n - 1) {//最后一个数据后不加空格
                printf(" ");
            }
        }
        printf("\n");
    }
    return 0;
}
```

# 排队

把前n个数放到后面

```c
void paidui(int arr[10], int n) {
	for (int i = 0;i < n;i++) {//循环n次
		int temp = arr[0];//把第一个数字放到杯子里
		for (int i = 0;i < 9;i++) {
			arr[i] = arr[i + 1];//所有数字往前移
		}
		arr[9] = temp;//把杯子倒进最后一个数里
	}
}
```

# 兔子问题

1，1，2，3，5，8，13，21，34，…
==从第三个数开始，等于前两个数之和==

```c
#include <stdio.h>
int main() {
    int T;
    scanf("%d", &T);
    while (T--) {
        int n;
        scanf("%d", &n);
        int arr[46] = { 1,1 };
        for (int i = 2; i < n; i++) {
            arr[i] = arr[i - 1] + arr[i - 2];
        }
        printf("%d\n", arr[n-1]);
    }
    return 0;
}
```

# 数位之和

<img src="C:\Users\35132\AppData\Roaming\Typora\typora-user-images\image-20240314001712512.png" alt="image-20240314001712512" style="zoom:67%;" />

```c
#include <stdio.h>
int main() {
	int n;
	while (scanf("%d", &n) != EOF) {
		int sum = 0;
		while (n != 0) {
			int temp = n % 10;
			n /= 10;
			sum += temp;
		}
		printf("%d\n", sum);
	}
	return 0;
}
```

# 找到数组中最小或最大的数以及下标

最小数是min，下标是min0

```c
int min = arr[0];
int min0;
for (int i = 0; i < n; i++) {
    if (arr[i] < min) {
        min = arr[i];
        min0 = i;
    }
}
```

# 统计字符个数

```c
#include <stdio.h>
#include <string.h>
int main() {
    char str[80];//定义一个存放字符串的字符数组
    scanf("%s", str);
    int sz = strlen(str);
    int count[128] = { 0 };//定义一个存放ASC码值的整形数组
    for (int i = 0; i < sz; i++) {
        count[str[i]]++;//遍历字符数组，0，0，0，0，0，1，0，0，0，2.............
    }
    for (int i = 0; i < 128; i++) {//遍历整形数组
        if (count[i] > 0) {
            printf("%c %d\n", i, count[i]);//i是下标，%c转化为字符，count[i]是次数
        }
    }
    return 0;
}
```

# 判断回文串

```c
#include <stdio.h>
#include <string.h>
int main() {
    int T;
    scanf("%d", &T);
    getchar();//吸收换行符
    while (T--) {
        char str[61];
        scanf("%s", str);
        int left = 0;
        int right = strlen(str) - 1;//stelen计算的是字符个数，不包括\0，这里要-1，才是下标
        int flag = 1;
        while (left < right) {
            if (str[left] != str[right]) {
                flag = 0;
                break;
            }
            left++;
            right--;
        }
        if (flag) {
            printf("Yes\n");
        }
        else {
            printf("No\n");
        }
    }
    return 0;
}
```

# 九九乘法表

![image-20240314174050740](C:\Users\35132\AppData\Roaming\Typora\typora-user-images\image-20240314174050740.png)

