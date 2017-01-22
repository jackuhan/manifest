# manifest
使用repo管理github项目例子

1、安装repo
mkdir ~/bin
export PATH=~/bin:$PATH
curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
brew install gnupg2

2、下载Android源码
repo init -u https//android.googlesource.com/platform/manifest
repo init -u https://android.googlesource.com/platform/manifest -b android-4.0.1_r1
repo sync
 
3、建立自己的repo:
http://gavinliu.cn/2016/04/15/Git-%E4%BD%BF%E7%94%A8Repo%E7%AE%A1%E7%90%86%E4%BD%A0%E7%9A%84Git%E9%A1%B9%E7%9B%AE/
先写default.xml文件保存到repo项目中，建立repo的github项目，推动xml文件提交
repo init -u git@github.com:jackuhan/manifest.git -b master
repo sync 
IOError: [Errno 2] No such file or directory: '/Users/hanjiahu/workplace/myRepo/.repo/manifest.xml'
复制上文件到.repo/manifest.xml并且改名。
repo sync #这样就可以下载在整个目录了，含有多个git仓库


Fetching project AndroidCountUpTimerView
Fetching project FlowlayoutTags
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:01 --:--:--     0
curl: (22) The requested URL returned error: 404 Not Found
Server does not provide clone.bundle; ignoring.
  0     0    0     0    0     0      0      0 --:--:--  0:00:01 --:--:--     0
curl: (22) The requested URL returned error: 404 Not Found
Server does not provide clone.bundle; ignoring.
remote: Counting objects: 162, done.        
remote: Counting objects: 98, done.         | 47.00 KiB/s   
remote: Total 162 (delta 0), reused 0 (delta 0), pack-reused 162        
Receiving objects: 100% (162/162), 378.98 KiB | 67.00 KiB/s, done.
Resolving deltas: 100% (41/41), done.
From https://github.com/jackuhan/AndroidCountUpTimerView
 * [new branch]      master     -> origin/master
Fetching projects:  50% (1/2)  remote: Total 98 (delta 0), reused 0 (delta 0), pack-reused 98        
From https://github.com/jackuhan/FlowlayoutTags
 * [new branch]      master     -> origin/master
Fetching projects: 100% (2/2), done.  

使用repo 批量管理 git 库
http://blog.sina.com.cn/s/blog_4e1e357d0102z4dw.html




<?xml version="1.0" encoding="UTF-8"?>
<manifest>
  <!-- remote: name 名称，fetch 远程地址。可以有多个remote，通过project.remote可指定不同的remote -->
  <remote name="origin"
          fetch="https://github.com/jackuhan/"
          review="https://github.com/jackuhan/" />
  <!-- default: revision 指定分支，remote 指定remote name，sync-j 同步线程数 -->
  <default revision="master"
           remote="origin"
           sync-j="4" />
  <!-- project：path 本地相对路径，name 远程相对路径，完整路径为 remote.fetch + project.name -->
  <project path="FlowlayoutTags" name="FlowlayoutTags" />
  <project path="AndroidCountUpTimerView" name="AndroidCountUpTimerView" />
</manifest>
