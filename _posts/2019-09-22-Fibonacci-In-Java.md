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
```java
    private long revFbncc(int n){
        count++;
        if(n <= 2 ){  //如果是 <=1 那就是 1，2，3，5，8 而不是 1，1，2，3，5，8
            return 1;
        }else{
            return revFbncc(n-1)+revFbncc(n-2);
        }
    }
``` 
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
