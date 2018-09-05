
### 开发问题汇集
- include、include_once 和 require、require_once 的区别
> include 函数：会将指定的文件读入并且执行里面的程序（失败返回 FALSE 并且发出警告；成功返回 1，除非在包含文件中另外给出返回值）；  
> require 函数：会将目标文件的内容读入，并且把自己本身代换成这些读入的内容（失败发出致命错误并终止程序；成功返回 1，除非在包含文件中另外给出返回值）；  
> include_once 函数：在脚本执行期间包含并运行指定文件。此行为和 include 语句类似，唯一区别是如果该文件中已经被包含过，则不会再次包含。如同此语句名字暗示的那样，只会包含一次（失败没有返回且发出警告；成功返回 True）；  
> require_once 函数：和 require 语句完全相同，唯一区别是 PHP 会检查该文件是否已经被包含过，如果是则不会再次包含（失败没有返回且发出致命错误并终止程序；成功返回 True）。  
>
> include 与 require 除了在处理引入文件的方式不同外，最大的区别就是：include 在引入不存文件时产生一个警告且脚本还会继续执行，而 require 则会导致一个致命性错误且脚本停止执行。  
> include 与 require 的功能相同，但在用法上却有一些不同，include 是有条件包含函数，而 require 则是无条件包含函数（即不论条件是否成立都包含到文件里）。  
> 
> include_once（require_once）语句在脚本执行期间包含并运行指定文件；  
> include_once（require_once）行为和 include（require）语句类似，区别是如果该文件中的代码已经被包含了，则不会再次包含，只会包含一次；  
> include_once（require_once）需要查询一遍已加载的文件列表, 确认是否存在, 然后再加载。  
> 通常，include_once 和 require_once 会有性能上的下降，因为他们需要判断之前是否包含过（实际上，也不太需要去考虑，除非这已经影响到你程序的性能了）。  
> 
> 如果使用 APC 尽量也不要用 include_once，因为 apc.include_once_override 配置项没有很好的被实现。  
>（Alternative PHP Cache (APC)是一种对PHP有效的开放源高速缓冲储存器工具，它能够缓存 php 的中间码 opcode）  
> 
> require 通常放在 PHP 程序的最前面，PHP 程序在执行前，就会先读入 require 所指定引入的文件，使它变成 PHP 程序网页的一部份。同时，也可以这个方法将它引入网页中。  
> include 通常放在流程控制的处理部分中。PHP 程序网页在读到 include 的文件时，才将它读进来。这种方式，可以把程序执行时的流程简单化。
> 
> return 语句在返回引用的时候加上括号不但效率低而且会造成逻辑错误。  
> 理论上，include 和 require 后面加不加括号对执行结果没有区别，但是加上括号效率较低，所以后面能不加括号就不加括号。  
> 

- 打开php.ini中的 safe_mode，会影响哪些函数
> safe_mode，php 安全模式，它提供一个基本安全的共享环境，在一个有多个用户账户存在的php开发的web服务器上  
> 当安全模式打开的时候，一些函数将被完全的禁止，而另一些函数的功能将会受到限制，  
> 如：chdir,move_uploaded_file,chgrp,parse_ini_file,chown,rmdir,copy,rename,fopen,require,mkdir,unlink 等。  
> 
> 注意，在 php5.3 以上版本，safe_mode 被弃用，在 php5.4 以上版本，则将此特性完全去除了。

- PHP 的垃圾收集机制 —— 引用计数  
> PHP可以自动进行内存管理，清除不再需要的对象。  
> PHP 使用了引用计数(reference counting)这种单纯的垃圾回收(garbage collection)机制，  
> 每个对象都内含一个引用计数器，每个 reference 连接到对象，计数器加 1。当 reference 离开生存空间或被设为NULL，计数器减 1。  
> 当某个对象的引用计数器为零时，PHP 知道你将不再需要使用这个对象，释放其所占的内存空间。

- 论坛中无限分类的实现原理
> 首先，创建类别表
```mysql
CREATE TABLE category(
cat_id smallint unsigned not null auto_increment primary key comment'类别ID',
cat_name VARCHAR(30)NOT NULL DEFAULT''COMMENT'类别名称',
parent_id SMALLINT UNSIGNED NOT NULL DEFAULT 0 COMMENT'类别父ID'
)engine=MyISAM charset=utf8;
```
> 编写一个函数，递归遍历，实现无限分类
```php
function tree($arr, $pid = 0, $level = 0)
{
    static $list = [];
    foreach($arr as $v){
        //如果父级分类一致，则将其存到 $list 中，并以此节点为根节点，遍历其子节点
        if ($v['parent_id'] == $pid){
            $v['level'] = $level;
            $list[] = $v;
            tree($arr, $v['cat_id'], $level + 1);
        }
    }

    return $list;
}
```

- 简述协程的优势
> 协程的特点在于是一个线程执行  
> 最大的优势就是协程极高的执行效率。因为子程序切换不是线程切换，而是由程序自身控制，因此，没有线程切换的开销，和多线程比，线程数量越多，协程的性能优势就越明显。  
> 第二大优势就是不需要多线程的锁机制，因为只有一个线程，也不存在同时写变量冲突，在协程中控制共享资源不加锁，只需要判断状态就好了，所以执行效率比多线程高很多。  
> 因为协程是一个线程执行，那怎么利用多核CPU呢？最简单的方法是多进程+协程，既充分利用多核，又充分发挥协程的高效率，可获得极高的性能。  

- 唯一 ID 的产生与方案
> 为什么要唯一 ID ?  
> 1、数据库的自增 ID 在分库的时候, 会是一场灾难。假设分两个库, 因为每个库都会开始从 1 开始自增, 这时候系统中将会出现两个 id 为 1 的用户  
> 2、自增 ID 会暴露用户量或者其他业务量  
> 3、自增 ID 会让有心者通过API得到任意用户的信息资料  
> 
> 有哪些解决方案呢?  
> 1、UUID，全称 Universally Unique Identifier，中文通用唯一标识符。这个是开放软件基金会组织提出的一个标准，为的就是解决分布式环境下生成唯一标识符的问题。  
> UUID 的长度是固定的 32 位，组织格式 8-4-4-4-12；当然，在用的时候，中间的分隔符是要去掉的。这货有几个问题不得不提，首先是字母数字混合，在一些传统数据库下，索引不太好做，不仅索引体积大， 查询效率也差，其次是它本身也非常大。  
> 2、 MongoDB ObjectId , 格式模样都很类似于 UUID，是 Mongodb 内置的一种数据类型，如果你在插入数据的时候不指定_id，那么 Mongodb 默认就会采用用这个货才填充_id， 在 Mongodb 这种类 key-value 性质的数据库中，有着不错的查询效率  
> 3、自建解决方案。需要保证全局空间唯一性、尽量采取数字类型而非数字字母混合方式、一定的时序行和含义、一定的可反解性 , 通过反解的结果可以知道该 ID 的相关信息。  
> 市面上有的几种解决方案为 Twitter 的 snowflake，Flikr 的数据库自增方案，Instagram 的数据库存储过程方案。  
> 比如 snowflask 使用了 64bit 来表示一个 id，组织格式 41(时间戳)-10(机器 ID)-12(自增序列)。推荐基于 snowflask 的 PHP ID 产生器：[DonkeyID](https://github.com/osgochina/donkeyid)  

- 自动加载与命名空间
> PSR4 利用了命名空间和 spl_autoload_register() 在 php-fig 的倡导下形成的一种开发者约定俗成的开发标准和规则。只要开发者开发的库满足 PSR 系列的标准，那么这个库就可以在任意一个支持 PSR 标准的任意框架或项目中运行，最终诞生了伟大的 php composer。  
> 
> 众所周知，php 中有个大名鼎鼎的魔法函数__autoload() 用来实现自动加载，但是__autoload 有个巨大的缺陷，就是无法同时加载多个 autoload 方法。  
> 于是，[spl_autoload_register()](http://php.net/manual/zh/function.spl-autoload-register.php) 来了，它可以注册多个 autoload 方法，即注册不同的自动加载机制。  
> 
> 命名空间，即 [namespace](http://www.php.net/manual/zh/language.namespaces.php)，是 php5.3 以后引入的新特性，用来解决包名冲突问题的。  
> 命名空间通常对应了文件夹目录的层次关系，当然这并不是官方的规定，而是人们利用命名空间做出的一种规范，为的是方便开发和协调。  
```php
// 声明三个不同加载函数
function autoload_1( $classname ){
  echo "autoload 1";
}
function autoload_2( $classname ){
  echo "autoload 2";
}
function autoload_3( $classname ){
  echo "autoload 3";
}

// 将三个不同的函数注册到 autoload 栈中
spl_autoload_register('autoload_1');
spl_autoload_register('autoload_2');
spl_autoload_register('autoload_3');
```

### 开发进阶路线

