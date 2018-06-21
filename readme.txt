1．  Git是一种分布式版本管理工具。与SVN的最大区别在于，用户在本机即可实现一套完整的版本管理，即不依赖网络实现本机的离线提交和离线历史纪录。

2．  SSH是一种基于应用层上的安全协议，用这种协议来实现本机和github的交互。有http和ssh两种交互方式，而ssh的方式可以实现免密码登录。

3．  在windows下如何实现ssh免密码登录呢？步骤如下：

1）设置Git的user name和email：

$ git config --global user.name "XXXX"

$ git config --global user.mail "XXXX@XXXX.com"

 

2）生成SSH密钥过程：
1.查看是否已经有了ssh密钥：cd ~/.ssh
如果没有密钥则不会有此文件夹，有则备份删除
2.生存密钥：

$ ssh-keygen -t rsa -C “XXXX@XXXX.com”
按3个回车，密码为空。

这样即可在C:\Users\admin\.sss文件下得到两个文件：id_rsa 和id_rsa.pub;

 

3）登录https://github.com/，如没有账户则注册登录进入。

登录进去之后，选择SSH and GPG Keys->New SSH key

Key的内容为id_rsa.pub里面的内容（可用word打开）

Title的内容可以自己任意指定

 

4）登录远程库的地址，例http://192.168.2.8，如没有账户则注册登录进入

登录进入之后，选择profile settings->SSH Keys->Add Key

Key的内容为id_rsa.pub里面的内容（可用word打开）

Title的内容可以自己任意指定

 

5）测试：ssh git@github.com

$ sshgit@github.com

Theauthenticity of host 'github.com (192.30.253.112)' can't be established.

RSA keyfingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.

Are yousure you want to continue connecting (yes/no)? yes

Warning:Permanently added 'github.com,192.30.253.112' (RSA) to the list of known hosts.

PTY allocationrequest failed on channel 0

Hichenle90! You've successfully authenticated, but GitHub does not provide shellaccess.

Connectionto github.com closed.

 

所有准备工作完成，可以开始使用github了

 

1）  生成本地仓库

进入对应的本地仓库的地址    cd D:\code

创建对应的目录并进去

mkdir tools

cd tools

初始化     git init

2）  获取远程仓库信息：

git remote add origin git@192.168.2.8:EmbededSW/tools.git

后面标蓝的字体是在对应的远程仓库地址如http://192.168.2.8上点project，然后点击你需要获取的project即可得到。

3）  git pull origin master

check下来对应目录下的最新代码。

$git pull origin master

Theauthenticity of host '192.168.2.8 (192.168.2.8)' can't be established.

ECDSAkey fingerprint is SHA256:8WOAgGk5o9fkEURIf6cNOJZUx/zkOlRB600XkLvJLsk.

Areyou sure you want to continue connecting (yes/no)? yes

Warning:Permanently added '192.168.2.8' (ECDSA) to the list of known hosts.

remote:Counting objects: 8, done.

remote:Compressing objects: 100% (6/6), done.

remote:Total 8 (delta 0), reused 0 (delta 0)

Unpackingobjects: 100% (8/8), done.

From192.168.2.8:EmbededSW/tools

 * branch            master     -> FETCH_HEAD

 * [new branch]      master    -> origin/master
 
 
 

 
echo "# AIPlatform" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:huangdeyun/AIPlatform.git
git push -u origin master