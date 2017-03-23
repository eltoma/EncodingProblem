# 关于编码的几个思考题

## 背景
- 使用c语言为描述语言(如果理解)
- 最好是能编程实现下(visual stdio下面可以调试c噢)
- `int` 型变量在内存中占4个字节

## 问题1
假设有一个变量`int a = ?`, 请问?等于多少时，a在内存中的布局会是以下的情况：
```
0110 0101 0110 1100 0111 0100 0110 1111
```

## 问题2
- 假设现在你已经完成了对a的正确赋值，现在要求你打印出这个变量在内存中的(二进制)布局情况。说明如下：
    - 如果某一位值为`1`，则打印字符`1`；如果某一位值为`0`，则打印字符`0`
    - 如果没错的话，程序的输出应该是：`0110 0101 0110 1100 0111 0100 0110 1111`
- 提示
    + 或许需要使用循环
    + 利用`printf("%d", int型变量)`可以打印一个整型变量的值

## 问题3
- 请将问题2中的打印形式转换为16进制
- 可以确定输出是：`65 6C 74 6F`

## 问题4
- 假设我调用`printf("%c", a)`,打印结果是什么？
- 提示
    + `"%c"`表示以8`bit`为单位处理 
    + 每个单元按ascii编码解释输入的数据内容
    + 有用的链接[ascii码查询](http://www.asciima.com/)


```java
public class Test {
    public static void main(String[] args) throws Exception {
        String a = "LAB108";
        byte[] bytea = a.getBytes("ASCII");
        
        int inta = bytea[0]<< 24;
        inta += bytea[1] << 16;
        inta += bytea[2] << 8;
        inta += bytea[3];
        
        StringBuilder str = new StringBuilder("");
        int i = 0;
        while(inta > 0) {
            temp = inta % 2;
            inta /= 2;
            i ++;
            str.append(temp);
        }
        System.out.println("\n" + str.reverse());
    }
}
```
