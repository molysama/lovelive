#编译vim并开启语言支持

##移除原有vim
```
sudo apt-get remove vim  
sudo apt-get remove vim-runtime  
sudo apt-get remove gvim  
sudo apt-get remove vim-tiny  
sudo apt-get remove vim-common  
sudo apt-get remove vim-gui-common
```

##解压安装包
```
tar -xjvf vim-7.4.tar.bz2
cd vim-7.4/src
```

##添加参数
```
./configure --prefix=/usr/local/vim74 --with-features=huge --enable-pythoninterp --enable-pythoninterp3 --enable-perlinterp --enable-rubyinterp --enable-luainterp --enable-multibyte --enable-sniff --enable-fontset --with-features=huge --enable-pythoninterp --enable-perlinterp --enable-rubyinterp --enable-luainterp --enable-multibyte --enable-sniff --enable-cscope
```

##参数说明

--prefix=/usr/local/vim74:编译安装路径  
--with-features=huge：支持最大特性  
--enable-pythoninterp：启用Vim对python编写的插件的支持  
--enable-pythoninterp：启用Vim对python3编写的插件的支持  
--enable-perlinterp：启用Vim对perl编写的插件的支持  
--enable-rubyinterp：启用Vim对ruby编写的插件的支持  
--enable-luainterp：启用Vim对lua编写的插件的支持  
--enable-multibyte：多字节支持 可以在Vim中输入中文  
--enable-sniff：Vim状态提示 提示Vim当前处于INSERT、NORMAL、VISUAL哪种模式  
--enable-cscope：Vim对cscope支持  
--enable-gui=gtk2：gtk2支持,也可以使用gnome，表示生成gvim  

##编译
```
sudo make
sudo make install
```
##重新编译
在./configure之前执行如下代码
```
make distclean
```

##添加搜索路径
```
vi /etc/profile

if [ "`id -u`" -eq 0 ]; then
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/vim74/bin"
else
  PATH="/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games:/usr/local/vim74/bin"
fi
export PATH

```

##常见错误及解决办法
no accetableC compile found in path  
```sudo apt-get install gcc```
