## 格雷码

​	在一组数的编码中，若任意两个相邻的代码只有一位二进制数不同，即海明距离为1，则称这种编码为格雷码（Gray Code），另外由于最大数与最小数之间也仅一位数不同，即“首尾相连”，因此又称循环码或反射码。

![1548999843129](C:\Users\WTF\AppData\Roaming\Typora\typora-user-images\1548999843129.png)

## 格雷码生成算法（减一法）

### 基本思想：

假设已经生成了k位格雷码，那么k+1位格雷码的生成方式为

(1) 按序在k位格雷码前插入一位0，生成一组编码

(2)按逆序在k位格雷码前插入一位1，生成另外一组编码

(3)两组编码合起来就是k+1位格雷码

![1548999889915](C:\Users\WTF\AppData\Roaming\Typora\typora-user-images\1548999889915.png)``

### 算法复杂度：

n位的格雷码数可以组成的格雷码串的个数为：2^n

第n次迭代需要执行基本运算的次数为：

n*2*2^(n-1)=n*2^n

时间复杂度为：

M(0)=1

M(n)=M(n-1)+n*2^n=M(n-2)+n*2^n+(n-1)∗2^(n-1)

=······=O(n2^n)

``

```
"""
反射格雷码的减一生成法
"""
import time
import os


class GrayCode():

    def getGray(self, n):
        global maxn
        maxn = n
        return GrayCode.getGrace(self, ['0', '1'], 1)

    def getGrace(self, list_grace, n):
        # print(list_grace)
        global maxn
        if n >= maxn:
            return list_grace
        list_befor, list_after = [], []
        for i in range(len(list_grace)):
            list_befor.append('0' + list_grace[i])
            list_after.append('1' + list_grace[-(i + 1)])
        return GrayCode.getGrace(self, list_befor + list_after, n + 1)


if __name__ == '__main__':
    n = input('请输入你所希望生成的格雷码的位数:')
    n = int(n)
    start = time.clock()
    gary = GrayCode()
    print(gary.getGray(n))
    end = time.clock()

    print("final is in ", round(end - start, 4), 's')
    print('author :tfflyer, you are not expected to see this')
    os.system("pause")
```

