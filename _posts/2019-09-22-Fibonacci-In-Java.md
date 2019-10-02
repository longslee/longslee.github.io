# ~~今天就到这里吧，睡觉了😪...~~
# 斐波拉契数列的几种实现方式及衍生问题
先把代码贴好?  
```java
  private long tailFbnc(int n,long a,long b){
        c++;
        if (n<=2) {
            return a;
        }
        return tailFbnc(n-1,b,a+b);
    }
```
这是最常规的递归写法。那这有什么不好的地方呢？是的，注意看这种算法，每次算高阶都要把高阶拆分为底阶重新算一次，复杂度会递增。

```java
    private long revFbncc(int n){
        if(n <= 2 ){  //如果是 <=1 那就是 1，2，3，5，8 而不是 1，1，2，3，5，8
            return 1;
        }else{
            return revFbncc(n-1)+revFbncc(n-2);
        }
    }
``` 
这种尾递归的方式，就是解决常规递归复杂度递增的改进，即把上一阶的结果缓存下来，以后计算直接使用。

*那么使用递归还会有什么问题呢？*
递归是交给机器去做了，但是对于JVM来说，线程中执行一个方法，就是一个入栈的过程，如果阶数特别大，而对应的线程栈空间又很小，那么会抛出StackOverflowError. 您可调大调小-Xss参数试试。

```java    
private long calFbncc(int n) throws Exception {
        if(n<0){
            throw new Exception("不能<0");
        }
        if( n==1 || n==0) return n;
        long a=0,b=1;  // a表示第一位虚0，b表示真正第一的1
        long sum=0;
        while (n>=2) {
            sum=a+b;
            a=b;
            b=sum;
            n--;
        }
        return sum;
    }
```
最后，就是常规的自己定义算法啦，虽然人参与其中，但是效率还挺高。
