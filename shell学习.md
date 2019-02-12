### shell学习

1. `~`代表当前用户目录,`/`代表顶层根目录

2. **逻辑判断:**

   ```bash
   # 严格要求保留空格
   if [ $var1 == $var2 ] 
   then
   	echo "do some thing"
   fi
   ```

3. `read 变量`指令可以将执行阻塞，等待命令行收到输入，将输入内容赋值到变量中

4. **循环:**

```bash
#遍历数字 指定循环次数
for i in {1..6}
do
	echo "$i"
done
#遍历数组
for i in $array
do
	echo "$i"
done
#遍历路径
for i in ~/* #遍历用户目录下所有内容，*为通配符
do 
	echo "$i"
done
#while循环
while boolean
do
	echo "some"
done
```

5. 声明:

```bash
#1. 数组
arr=(1 2 3)
#2. 函数
sayHi(){
    echo "$1 $2"
}
sayHi 变量1 变量2
```

> 调用文件时传参与函数传参类似 `sh lean-about-shell.sh  参1 参2`

6. 读取写入文件

```bash
#1. 读取 获取指令输出的值使需要使用反引号注释
for Line in `cat path`
do 
   echo $Line
done
#2. 写入
echo something > path
#3. 追加
echo something >> path
```

