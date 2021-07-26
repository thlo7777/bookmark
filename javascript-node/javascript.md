#### 1. 修改this指向
修改this指针有三种方法：
bind apply call
其中 apply和call都是立即执行的，只有bind是将修改this指针后，返回一个新的函数，不会立即调用
apply和call的区别主要是，apply只接收数组形式的参数输入 
