---
layout: post
title: '插件开发经验之如何运用 C::t 方法(转载)'
---
抽点时间讲解一下C::t方法的简单使用。
一、C::t方法的好处：一是对象清楚，二是对形参格式化处理，三是可集中SQL语句，利于维护，四是安全性更高。
二、具体用法，看下面的例子
假设有一个名为test的插件，其中关于名为tbname的数据表操作的SQL
旧式写法
a.inc.php

```php
<?php
……
$query = DB::query('select * from '.DB::table('tbname').' where id='.$id);
while($v = DB::fetch($query)){
……
}
……
?>
```

改造为C::t如下
a.inc.php

```php
<?php
……
$query = C::t('#test#tbname')->fetch_all($id);
foreach($query as $key => $value){
或者将上面的两行变为一行，以减少行数，如下
foreach(C::t('#test#tbname')->fetch_all($id) as $key => $value){
……
}
……
?>
```

再新建一个文件夹名为table，放在插件根目录下，在table中创建一个名为table_tbname.php的类文件(详见技术文库的相关说明)，该文件的代码框架如下
table_tbname.php

```php
<?php
if (!defined('IN_DISCUZ')) {
    exit('Aecsse Denied');
}
class table_tbname extends discuz_table{
    public function __construct() {
        $this->_table = 'tbname';
        $this->_pk = 'id';
        parent::__construct();
    }
    /*------------在此处构造N多的自定义函数，本例中自定义的函数如下-------------*/
    public function fetch_all($id){
         return DB::fetch_all('select * from %t where id=%d',array($this->_table,$id));
    }
}
?>
```


C::t的运用有很多变化，但万变不离其宗，基本骨架就是上面的样子。
注意：
1、自定义函数中有一个同名函数名fetch_all，虽然名字相同，但内涵不同。本例比较特殊，实际自定义函数名称你可以随便起，例如public function ldsjglfdjs($id)，不一定非要像技术文库要求那样规则命名，当然，规则命名更易于辨认理解维护
2、SQL中应当用格式化语句书写，以保障安全性，其中的%t代表了对数据表名的格式化，%d代表了对%id的格式化，其中的含义请查询技术文库"源DB类的改进"，以了解掌握都有哪些格式符及其意义并加以运用。这里要特别注意%s和%i的区别，涉及安全处理问题
3、虽然不是必须，但我仍建议并强调，以数组形参的形式作为DB层封装函数的第二参数(如果该函数有此参数的话)，例如上例中的DB::fetch_all(SQL,array(第一形参,第二形参,...))，某些DB层封装的函数对于有无$arg这个数组参数有着不同的执行过程，将会影响对该参数中的变量是否进行安全过滤的行为
4、SQL中的格式符一定要和数组形参中的变量一一对应，不能颠倒
5、不提倡旧式的SQL写法，如DB::fetch_all('select * from '.DB::table('tbname').' where id='.$id)，原因见上面的3
6、虽然不是必须，但C::t方法中自定义函数内最好不要使用诸如$_GET、$_POST之类的全局变量，应在C::t之前赋值后传入，否则，例如在DB::query中使用，如不进行过滤，其安全性将难以保障
7、大多数被DB封装的常用数据库操作函数，其参数都将被做安全处理，因此要注意，虽然不是必须避免重复过滤，但应考虑执行效率问题。
8、注意注意再注意，由于大多数被DB封装的常用数据库操作函数都要调用内部query函数，相当于在外部直接使用DB::query，而该函数有个特例情况，就是上面3所说，因此特别要考虑有无数组形参，进而加固安全性
9、尽量将SQL集中放在C::t方法的类文件中，避免在应用层等其他文件中使用SQL，这样能使对象更清晰规范方便维护

官方在source/class/table中已经内置了很多C::t方法，假设在插件设计时所用的方法是官方所没有的，而官方已创建了一个同名类文件，这时怎么办？那就按上面例子所示，自己创建一个同名类文件就行了，但应用层一定要用C::t('#插件标识符#不带前缀的表名')来调用，而不是C::t('不带前缀的表名')这种方式

闲暇之余多看看source/class/discuz中的discuz_database.php和dizcuz_table.php这两个重要文件，烂熟其中被DB封装的常用函数的执行原理和机制，对自如运用C::t和加强安全认识有好处
转载地址：[http://www.discuz.net/forum.php?mod=viewthread&tid=3448677](http://www.discuz.net/forum.php?mod=viewthread&tid=3448677)
