
RVM 是一个命令行工具，可以提供一个便捷的多版本 Ruby 环境的管理和切换。
https://rvm.io/

rvm是用来管理ruby的，ruby的其中一个“程序”叫rubygems，简称 gem，而用来管理软件包（代码库）


RVM 安装 

```bash
$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
$ \curl -sSL https://get.rvm.io | bash -s stable
$ source ~/.bashrc
$ source ~/.bash_profile
```

修改 RVM 的 Ruby 安装源到 Ruby China 的 Ruby 镜像服务器，这样能提高安装速度
```bash
$ echo "ruby_url=https://cache.ruby-china.org/pub/ruby" > ~/.rvm/user/db
```

Ruby 的安装
列出已知的 Ruby 版本
```bash
rvm list known
```
安装一个 Ruby 版本
```
rvm install 2.4.1 --disable-binary
```

gollum的安装
```
gem install gollum
```

apt-get install libicu-dev

icu required (brew install icu4c or apt-get install libicu-dev)


https://github.com/xilibi2003/learnblockchain.git
git@github.com:xilibi2003/learnblockchain.git


    index index.html index.htm index.txt;
    root /home/run/simple/_book;
    access_log  /home/run/web_log/learnblockchain.log;
    error_log   /home/run/web_log/learnblockchain.log warn;



/home/run/learnblockchain.wiki/_book

        // "-lunr",
        // "-search",
        // "search-pro",
        // "theme-official",