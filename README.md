# Automatic_Generation_Operation
自动生成练习题

# 其中的Arithmetic.java为项目源码（新手入门）





### 软件基本功能如下

1. 自动生成10道100以内的2个操作数的四则运算算式（+ - *  /），要求运算结果也在100以内

2. 剔除重复算式。  2 + 3 =    和  2 + 3 =     是重复算式      2 + 3 =   和   3 + 2 =  不属于重复算式

3. 题目数量可定制

4. 相关参数可控制
    是否包含乘法和除法
    操作数数值范围可控（如操作数 在100以内   还是1000以内）
    操作数是否含负数　　　　

5. 生成的运算题存储到外部文件result.txt中

### 一、需求分析

#### 1.对产品功能的需求：

- 自动生成10道2个操作数的四则运算算式
- 没有重复的算式
- 题目数量可控
- 相关参数可控
- 将生成的题保存到外部文件中

#### 2.对产品开发过程的需求：

- 使用C语言或者Java
- 保存算式题并生成文件

### 二、功能设计

1.基本功能

- 题目数量可任意定制
- 二则运算和四则运算可选
- 操作数范围可控
- 包含正负数可选
- 重复算式可过滤

2.扩展功能

- 答案是否需要打印


### 三、设计实现

- 本次程序设计只用到一个主类，其中包含了主方法和其他方法共同实现程序的相关功能。
    - 判断是否需要负数的方法
    - 判断是否需要包含乘除的方法
    - 获取随机数的方法
    - 获取算式得数的方法
    - 主方法



### 四、测试运行

- 测试一：无负数四则运算

<img src="https://img2018.cnblogs.com/blog/1791075/201909/1791075-20190912121230078-286315019.png" width="100%" height="100%" />

- 测试二：有负数二则运算

<img src="https://img2018.cnblogs.com/blog/1791075/201909/1791075-20190912123135671-1907393900.png" width="100%" height="100%" />


### 五、代码片段

- 过滤重复算式代码块

```
if(resultz <= max_toprange && resultz >= -max_toprange){
        // 过滤重复算式
        if(i == 0){//第一题存入
        numx[i] = a;
        numc[i] = operator;
        numy[i] = b;
        numz[i] = get_result(a, operator, b);
        i++;
        }else{
            for(int j = 0;j < i;j++){//第二题开始与之前每一道做比较				 
                if (a!=numx[j]||operator!=numc[j]||b!=numy[j]) {
                    numx[i] = a;
                    numc[i] = operator;
                    numy[i] = b;
                    numz[i] = get_result(a, operator, b);
                }else{
                    fl--;//如果有重复多加一道
                }
            }
            i++;         
        }
        fl ++;
}
```

- 判断是否包含乘除法

```
static char need_MulandDiv(int flag){
	char x = 0;
	if(flag == 1){
    	char[] ch = {'+','-','*','/'}; //字符数组
    	Random r = new Random();
    	int index = r.nextInt(ch.length); //随机数，小于数组的长度数, 0~3
    	x = ch[index];//打印随机字符 
    }else if (flag == 0) {
    	char[] ch = {'+','-'}; //字符数组
    	Random r = new Random();
    	int index = r.nextInt(ch.length); //随机数，小于数组的长度数, 0~1
    	x = ch[index];
    }
	return x;
}

```

- 判断是否包含负数

```
static int need_Negative(int flag, int max){
	//如果需要负数，则最小值为100
    if(flag == 1){
    	min = -max;
    }
    //int randNumber =rand.nextInt(MAX - MIN + 1) + MIN;将被赋值为一个 MIN 和 MAX 范围内的随机数
	return (max - min + 1);
}

```




### 六、总结

- 通过本次练习，又学到了许多知识。经过一步步需求分析到功能的一步步实现，虽然遇到了些许挫折，但收获也是颇丰。

- 看似只是出几道四则运算题，其实其中需要注意的细节也非常多，时间仓促，以后会慢慢改进。




