# MAMP编译安装拓展

###### 1. 下载对应拓展,进入拓展
```
如果是git/svn迁出的代码需要执行代码根目录的buildconf脚本以生成所需要的构建脚本。
```

###### 2. 执行 phpize
```
/Applications/MAMP/bin/php/php7.2.7/bin/phpize

什么是phpize? phpize是编译PHP扩展的工具，主要是根据系统信息生成对应的configure文件
```

###### 3. 执行 ./configure 

```
./configure --with-php-config=/Applications/MAMP/bin/php/php7.2.7/bin/php-config

什么是./configure? 这一步一般用来生成 Makefile，为下一步的编译做准备，你可以通过在 configure 后加上参数来对安装进行控制，比如代码:./configure –prefix=/usr 意思是将该软件安装在 /usr 下面，执行文件就会安装在 /usr/bin （而不是默认的 /usr/local/bin),资源文件就会安装在 /usr/share（而不是默认的/usr/local/share）。同时一些软件的配置文件你可以通过指定 –sys-config= 参数进行设定。有一些软件还可以加上 –with、–enable、–without、–disable 等等参数对编译加以控制，你可以通过允许 ./configure –help 察看详细的说明帮助。
```

###### 4. make clean 

```
删除源代码（C\C++ code）生成的执行文件和所有的中间目标文件
```

###### 5. make 编译
  
```
make

这一步就是编译，大多数的源代码包都经过这一步进行编译（当然有些perl或python编写的软件需要调用perl或python来进行编译）。如果 在 make 过程中出现 error ，你就要记下错误代码（注意不仅仅是最后一行），然后你可以向开发者提交 bugreport（一般在 INSTALL 里有提交地址），或者你的系统少了一些依赖库等，这些需要自己仔细研究错误代码。
```

###### 6. make install 安装


