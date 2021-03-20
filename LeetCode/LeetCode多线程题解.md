+ ## [玩转Leetcode多线程——JAVA线程协助工具类实战](https://zhuanlan.zhihu.com/p/81626432)
+ ## java多线程什么情况下线程会让出CPU
> sleep()，yield(),wait(),await(),线程结束
>> Thread.sleep(); <br/>
sleep就是正在执行的线程主动让出cpu，cpu去执行其他线程，在sleep指定的时间过后，cpu才会回到这个线程上继续往下执行， **如果当前线程进入了同步锁，sleep方法并不会释放锁，即使当前线程使用sleep方法让出了cpu，但其他被同步锁挡住了的线程也无法得到执行。**<br/>
在多线程争用的情况，拥有锁的线程进行一些耗时操作，会极大降低吞吐量（amdahl定律），**如果在同步块中使用sleep就是一种糟糕的做法，它不会释放锁却阻止其他线程获得锁。**

>> Thread.yield();
yeild是个native静态方法，这个方法是想把自己占有的cpu时间释放掉，然后和其他线程一起竞争(注意yeild的线程还是有可能争夺到cpu，注意与sleep区别)。**在javadoc中也说明了，yeild是个基本不会用到的方法，一般在debug和test中使用。**

>>Object.wait();<br/>
wait会把当前的锁释放掉同时阻塞住，让出CPU；当别的线程调用该 Object 的 notify/notifyAll 之后，有可能得到 CPU，同时重新获得锁。<br/>
当然同样的
condition.await();
也会释放锁并且让出CPU；

>>当然很多竞争锁失败的线程最终也会阻塞住，但是这不是主动让出CPU，不在讨论范围内。