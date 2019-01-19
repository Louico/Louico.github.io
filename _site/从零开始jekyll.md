# 尝试将jekyll安装到github上
##遇到的第一个问题
You don't have write permissions for the /Library/Ruby/Gems/2.3.0 directory.
mac有自己的ruby 所以要安装到local中一个自己的版本
安装之后根据homebrew的提示 设置环境变量
echo 'export PATH="/usr/local/opt/ruby/bin:$PATH"' >> ~/.bash_profile
安装了本地的gem和ruby之后 gem install jekyll 但是失败
ERROR:  Error installing jekyll:
	ERROR: Failed to build gem native extension.
尝试安装xcode的command line tools 
使用命令
xcode-select --install
安装
问题依旧
 error: unknown type name 'uint8_t'
        uint8_t  ri_uuid[16];
使用命令 rm -rf /usr/local/include 清除了C++头文件目录 不太懂具体原理 应该是之前编译器的设置发生了混乱冲突 在升级到Mojave之后一些头文件需要重新安装 参考：https://github.com/mattn/go-sqlite3/issues/653
施行命令之后安装成功
却无法实施 jekyll
zhangxiaoyaodeMac-mini:Louico.github.io zhangxiaoyao$ gem which jekyll
/usr/local/lib/ruby/gems/2.6.0/gems/jekyll-3.8.5/lib/jekyll.rb
zhangxiaoyaodeMac-mini:Louico.github.io zhangxiaoyao$ jekyll
于是运行 gem environment命令 找到 - EXECUTABLE DIRECTORY: /usr/local/lib/ruby/gems/2.6.0/bin 行
运行
zhangxiaoyaodeMac-mini:Louico.github.io zhangxiaoyao$ echo 'export PATH="/usr/local/lib/ruby/gems/2.6.0/bin:$PATH"' >> ~/.bash_profile
zhangxiaoyaodeMac-mini:Louico.github.io zhangxiaoyao$ jekyll
-bash: jekyll: command not found
zhangxiaoyaodeMac-mini:Louico.github.io zhangxiaoyao$ source ~/.bash_profile
将其加入环境变量 jekyll可以运行
