参照官网上很简单的一句安装命令，
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
安装完毕后，发现使用brew命令，却总是提示：-bash: brew: command not found

于是怀疑安装过程出现问题，打算重装，重装却报：
the Homebrew installer has moved! Please instead run: ruby -e "$(curl -fsSL raw.githubusercontent.com/Homebrew/install/master/install)&q‌​uot; Also, 
please ask wherever you got this link from to update it to the above
琢磨了一番还是无解，于是仔细找了各种版本解决方式，都无果。终于在
http://stackoverflow.com/questions/14288682/error-installing-homebrew-brew-command-not-found
找到解决方式。其实解决这个问题真的很简单。如下：
sudo vim .bash_profile
添加：
export PATH=/usr/local/bin:$PATH
保存，source .bash_profile使配置修改生效。
再次使用brew 命令就ok了。
