C++
#interview-summary
1、malloc和new,free和delete区别
2、内存分类（堆、栈、text程序段，texy，全局数据段）
3、static作用（普通变量前加static,函数前加static,成员函数前加staic,第三种也就是静态成员函数成员函数和普通成员函数区别，静态成员变量和普通成员变量区别）
4、变量声明与定义 int a; int a=5;区别
5、extern作用
6、const作用（const int a, int const *p, const int *p,成员函数加const定义）
7、template模板声明和定义都写在.h文件
   因为要进行实例化模板函数和类模板，要求编译器在实例化模板时必须在上下文中可以查看到其定义实体
8、虚函数实现机制（虚函数表）
    有虚函数类的对象在调用构造函数时会生成虚函数表，在运行时，会根据对象类型将指针指向父类还是子类，然后调用相应的方法。
9、子类和父类构造函数析构函数顺序
  构造先父类变量在子类，析构先子类在父类。
10、公有继承和私有继承用处
11、什么是纯虚函数以及作用
12、子类对象在内存中存储方式？

网络：
1、为什么网络分层？网络层和传输层区别？
2、TCP建立三次握手过程？
3、TCP与UDP区别？

编译
1、编译和链接作用？
2、静态库和动态库区别？


系统
1、系统调度作用？
2、线程和进程区别？
3、线程有哪些状态？（就绪、执行、阻塞、挂起）
4、线程同步方法？
5、什么死锁？为什么会出现？


补充：
1、用户态切换到内核态的3种方式
a.  系统调用
b.  异常
c.  外围设备的中断 

2、注意指针加1操作，要根据指针类型来
   int a[10] = { 1,2,3 };
	int *p = a;
	cout << *(p+1) << endl; //p地址向前挪了四位
   输出2
3、char a[10]; sizeof(a)=10;
  char *p=a; sizeof(p)=4;
4、void hello(char a[])等价于 void hello（char *a)


二面题：
1、条件变量用法举例？
   条件变量通常和互斥量一起使用:原因互斥锁的保护下使用相应的条件变量。否则对条件变量的解锁有可能发生在锁定条件变量之前，从而造成死锁
   pthread_mutex_t fill_mutex=PTHREAD_MUTEX_INITIALIZER;
   pthread_cond_t cond_var=PTHREAD_COND_INITIALIZER;
  线程A:pthread_mutex_lock(&fill_mutex); 
	pthread_cond_signal(&cond_var); or pthread_cond_broadcast(&cond_var);
	pthread_mutex_unlock(&fill_mutex);
  线程B:pthread_mutex_lock(&fill_mutex);
  	while(condition_is_false)	
		pthread_cond_wait(&cond_var,&fill_mutex);
	pthread_mutex_unlock(&fill_mutex);

2、线程安全：在同一个时间点，函数可以被不同线程安全的调用。返回数据存放在内存缓存区中不是线程安全的。
   可重入的函数一般是线程安全的。
   
3、string对象末尾有一个是空字符
  eg.string teststr="SH"; teststr[2]='\0'; 
 
 金融公司面试（c++岗）
 电话面试：
 1、预处理阶段做什么？ 宏替换，条件编译处理，头文件包含展开
 2、linux错误日志放在什么位置？var/log目录下？
 3、哈希表hashmap数据结构?
 4、解释下设计模式中观察者模式？
    当对象间存在一对多关系,其他对象依赖摸一个对象，当这个对象修改时候，会通知其他对象，适合使用观察者模式。
    优点：观察者和被观察者是抽象耦合的。
    缺点：通知一个一个对象通知过去，浪费时间；当存在循环依赖时候，耦合性太高，存在循环调用，有可能导致崩溃。
 5、设计模式中的享元模式 ？
   共享对象,在某些对象需要重复创建，且最终只需要得到单一结果的情况下使用
数据库问题：
1、数据库中的事务含义？
   事务是指一次执行多个命令。事务需要满足条件：
   ..批量操作在发送 EXEC 命令前被放入队列缓存
   ..收到 EXEC 命令后进入事务执行，事务中任意命令执行失败，其余的命令依然被执行
   ..在事务执行过程，其他客户端提交的命令请求不会插入到事务执行命令序列中
 2. acid 函数  a(原子性) c(一致性) i(隔离) d(可持久化)
 3.SQL四种连接？内连接,左连接，有连接，完全连接。
 4、非关系型数据库和关系型数据库区别即优缺点？
   关系型数据库：使用关系模型来组织数据;支持acid
   		
		
		
   非关系型数据库：非关系型、分布式、不提供ACID的数据库设计模式;分布式.
   		 优点：
		 高性能读写;基于键值对，无耦合；存储形式丰富，键 - 值对存储，列存储，文档存储，图形数据库
		 缺点：
		 不支持sql

C++中函数签名不包括函数返回值，但是包括函数后的const的，也就是说重载的时候，仅凭函数返回值不同编译器是不区别的，也就是不行的，但是有无const是可以的，编译器区别的。
第一组：编译器报错
int fun(int a,int b)()
char fun(int a,int b){}
第二组：可以编译通过
int fun(int a,int b)
int fun(int a,int b) const






 
