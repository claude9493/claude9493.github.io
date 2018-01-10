---
layout: post
title: Basic MATLAB I
excerpt_separator:  <!--more-->
---
<!-- <h1>Basic MATLAB I</h1> -->
Here is part of my notes of matlab taken in the Greencity summer camp. May it helpful to you.<br/>
- 退出matlab
	- quit
	- exit
- 可以保存工作空间，之后恢复当前状态
- 命令窗功能键
	- Esc 删除光标所在行的全部内容
	- Ctrl+k 删除光标到行尾的内容
	- Ctrl+c 强行终止程序的运行
<!--more-->
- 帮助
	- help 显示注释
	- type M-文件名
	- lookfor 关键词：显示一批含有关键词的命令
	- who：显示工作空间所有变量名称
	- whos a b：显示工作空间中a,b变量的详细信息
	- what：列出当前目录或指定目录下的m文件、mat（数据文件）、mex（16进制文件）文件
	- dir：显示当前目录下的文件或子目录名称
	- ver：显示matlab的全部工具箱
	- path：设置matlab的搜索路径
	- cd：查询或改变路径
	- which m-文件名：显示该文件所在子目录的路径
- 储存与调出
	- save：储存工作数据
	- load：调用工作数据
- MATLAB 区别大小写
- MATLAB数据类型
	- 数值型数据
		- 整数
			- 有/无符 1/2/3/4字节整数
			- int8(), int16(), int32(), int64()  //强制类型转换
			- uint8(), uint16(), uint32(), uint64()
		- 浮点数
			- double() 双精度
			- single() 单精度
		- 复数
			- i或j都可以表示虚部单位
		- inf（无穷大，-inf）和NaN（非数值，Not a Number）
	- 字符串型数据
		- 'This is a string, 1+1=2 plot(x.^2) will not be ploted in string'
		- 通常可与符号型通用？？？
	- 符号型数据
		- sym(数字, 字符串, 字符变量名, 字符表达式)
		- syms a1 a2 a3
	- class(a)
- 变量名及赋值
	- 变量名=数据或已赋值过的变量名
- 数据的显示
	- disp(Zf)
		- 若Zf是字符，原样显示
		- 若Zf是变量名，显示其代表的值
	- 相当于print()


- 数值矩阵
	- 数值矩阵的基本形式是复数矩阵，数值、向量或实数矩阵都可以看做复数矩阵的特例
	- pi，eps，ans，INF，Inf，inf，i，j，NaN
	- 数值矩阵的创建
		- 直接输入元素
			- 元素置于[]内
			- 分隔符（行内元素用,或空格间隔），间隔符（行与行之间用;或回车间隔）
			- 续行号（输入没完成需要中途换行）...链接两行，不可以加在矩阵一行当中两个元素之间。
			- 矩阵元素，每行元素个数相同
		- <h6 color='red'>a=[a;1,2,3] 加一行123，a=[a,[1;2;3]] 加一列123</h6>
		- 特殊矩阵
			- zeros(n),zeros(m,n)全零阵
			- ones(n),ones(m,n)全一阵
			- eye(n)输出一个n阶的单位方阵
			- rand(n)，rand(m,n)元素满足均匀分布的随机矩阵
			- randn(n),randn(m,n)元素满足正态分布的随机矩阵
			- magic(n)魔方阵
			- diag(a,k)取a矩阵的主对角线右移k列构成的列向量，k可省略
			- tril(a)矩阵a主对角线下方元素构成的三角阵
			- triu(a)矩阵a主对角线上方元素构成的三角阵
	- 变化矩阵结构
		- flipud(A)上下对称，ud:up&down
		- fliplr(A)左右对称  lr:left&right
		- rot90(A,k),rot90(A)矩阵A沿着逆时针方向旋转k个90度
		- reshape(A,m,n)将A变为m*n矩阵(元素总数不变)，保持元素序号不变(matlab中元素序号先列后行）
		- >E.x.<br>
		d=[[4:-1:1];[8:-1:5]]<br>
		d =<br>
	     	4     3     2     1<br>
     		8     7     6     5<br>
		d=rot90(reshape(1:8,4,2),-1)<br>
		d =<br>
     		4     3     2     1<br>
     		8     7     6     5<br>

	- 特殊向量的创建
		- 等差数列
			- 增量输入法:t=start:step:end OR t=[start:step:end] OR t=(a,h,b) 产生的数列终点不一定是b
			- 指令输入法:t=linspace(a,b,nodes=100等分a到b的节点数默认100) 把a和b之间等分了n-1份，长度是n
		- 等比数列：q=logspace(as,bf,nodes=50) 初值为as终值为bf的50个数的等比数列 在10的as次方和10的bf次方之间按照对数距离等间距产生n个数
		- ones(1,n),linspace(1,1,n),logspace(0,0,n)
	- 数值矩阵元素的切片与修改
		- a(p) a矩阵当中序号为p的元素，a(:) a中所有元素按照先列后行排成一个列矩阵
		- a(m,n) 第m行n列的元素,a(:,n) 第n列的所有元素构成的列向量，a(m,:) 第m行所有元素构成的行向量
		- a(m,[p,q,r]) a中第m行第pqr列元素构成的行向量
		- a(p:q,n) a中第n列第p到q行的元素构成的列向量
		- a([p,q,r],[w,s]) 构成3*2的矩阵
		- a(m,:)=[], a(:,n)=[] 删除第m行/n列

- 数值矩阵的矩阵算法和数组算法
	- **矩阵**算法
		- 一元运算
			- sime(a) 查验矩阵A的维度， size(a,r) 
			- A' 共轭转置，conj(A) 共轭， 转置要两步
			- inv(A) 求方阵的逆, pinv(B) 求矩阵的伪逆阵(B非方阵，xbx=b & bxb=x, x为b的伪逆阵)
		- 二元运算
			- +-*, mtimes(A,B)
			- a^n, mpower(a,n) 矩阵a的n次方，n小于零则为a的n次方的逆
			- a+d=a+d*ones(size(a)) 矩阵加减常数
			- x=inv(a)*b x=a\b (b÷a) mldivide(a,b) 左除
			- x=b*inv(a) x=b/a (a÷b) mrdivide(b,a) 右除
		- 矩阵函数（只针对方阵）
			- expm(A): e的A次方, logm(A): 以e为底A的对数, sqrtm(A): A的平方根
			- funm(a,@f): 自定义函数
	- **数组**算法
		- length(A) 向量输出维数，列阵输出列数，矩阵输出max{列数,行数}(i.e. length(A)=max(size(A)  )
		- 参与数组运算的矩阵维数必须严格相同
			- a.*b (对应位置相乘), a.^n (对应位置n次方), a./s = s.\a a中每个元素除s, s./a = a.\s s被a中每个元素除, a./b = b.\a a中元素除b中对应元素
	- 矩阵算法不遵从交换律，矩阵的数组乘法遵从交换律
	- 其他
		- real() imag() abs() 
		- mean() sum() sign()
		- pow2() 平方 sqrt() 开根号
		- round()四舍五入，floor()输出靠近负无穷的整数，ceil() 输出靠近正无穷的整数，fix()输出靠近0的整数
		- prod(m,n) 求Cmn组合数  factorial(x) 阶乘
	- dot(a,b) 点乘，cross(a,b) 叉乘
