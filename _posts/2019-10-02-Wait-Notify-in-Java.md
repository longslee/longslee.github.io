# 照例先抛出title再写
  我们都知道，在JAVA中，调用一个对象的notify or notifyAll，会通知在这个对象上等待的线程进行返回。那么使用wait和notify的前提是什么呢？
  那就是使用前必须要获取这个对象的锁，准确说是该对象的监视器？否则会报出 java.lang.IllegalMonitorStateException.
