#软件使用
  ##v2ray
    https://toutyrater.github.io/prep/install.html 
    https://github.com/233boy/v2ray/wiki/V2Ray%E4%B8%80%E9%94%AE%E5%AE%89%E8%A3%85%E8%84%9A%E6%9C%AC 
  ##Nginx
  一、启动
  
     cd usr/local/nginx/sbin
     ./nginx
  二、重启
    更改配置后重新加载配置
    先判断配置文件是否正确
    
    nginx -t -c /usr/local/nginx/conf/nginx.conf
    或者
    cd /usr/local/nginx/sbin
     先./nginx -t或者nginx -t
    后./nginx -s reload 或者 service nginx reload
    
   如果有报错
     
     nginx: [error] open() "/usr/local/nginx/logs/nginx.pid" failed (2: No such file or directory)
     使用nginx -c的参数指定nginx.conf文件的位置
     /usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf
  三、关闭
    
    查询nginx主进程号
    
    ps -ef | grep nginx
    
    从容停止 kill -QUIT 主进程号
    
    快速停止 kill -TERM 主进程号
    
    强制停止 kill -9 nginx
    
    若nginx.conf配置了pid文件路径，如果没有，则在logs目录下
    
    kill -信号类型 '/usr/local/nginx/logs/nginx.pid'

  ##myComputer
   ###node
    node 目录
    node: /usr/bin/node /usr/local/bin/node /usr/local/application/nodeJs/bin/node

   ###jenkins
    jenkins配置目錄
    /etc/sysconfig/jenkins
    
    jenkins项目地址I
    /var/lib/jenkins/workspace/super/client/dist
    /var/lib/jenkins/workspace/superServer/server
    /var/lib/jenkins/workspace/mango/_book;
    
    jenkins重启
    http://localhost:8080/restart 
    http://localhost:8080/reload 
    service jenkins start
    service jenkins restart
    service jenkins stop

   ###forover
    forever默认安装位置在/usr/bin下
    forever start app.js
    //关闭命令
    forever stop app.js
    //重启命令
    forever restart app.js

   ###nginx
    /usr/local/nginx
   ###在jenkins中部署工程时进行构建的处理
        #!/bin/bash -ilex  这个可以获取所有的权限
        cd server 
        #bash reload.sh
        ssh -l root 123.206.62.148 'cd /var/lib/jenkins/workspace/superServer/server; ./reload.sh'  以root的身份执行sh文件
        
        cp /var/lib/jenkins/workspace/superServer/server/reload.sh /var/lib/jenkins/workspace/mango/reload.sh  copy文件
        
        ssh -l root 123.206.62.148:65534 'cd /var/lib/jenkins/workspace/mango; ./reload.sh'
        #!/bin/bash -ilex
        /var/lib/jenkins/workspace/mango/reload.sh
        
        gitbook -V
        #ssh -l root 123.206.62.148 -p 65534 "/var/lib/jenkins/workspace/mango/reload.sh"
        
        ln -s /usr/local/application/nodeJs/bin/gitbook /usr/local/bin/gitbook    
        把gitbook加到环境变量中要不在jenkins中构建部署执行shell时，会失败
        
        setsid gitbook serve  启动gitbook并保持不停止

   ### IDEA
   ##### 插件
    智能代码提示：codota，
    快捷键提示：Key-Promoter-X，
    lombok-plugin，
    MavenRunHelper，
    将json转换为模型对象：RoboPOJOGenerator，
    项目类型统计：Statistic
   ###谷歌浏览器
   ####浏览器插件
   >Tablist
   
    查看打开的所有网页链接一键复制或者选择复制
   > adblock
   
    在YouTube、Facebook、Twitch和其他你喜爱的网站上拦截广告和弹窗。
   >idm

    一个页面集成下载器
   >JSONView
    
    查看页面json文件格式化
   >OneTab
   
    节省高达95％的内存，并减轻标签页混乱现象
   >捕捉网页截图
   
    捕捉网页截图，编辑并将它们保存为PDF，JPEG，GIF，PNG或BMP；上传，打印，在Photoshop中打开，复制到剪贴板或电子邮件
   >极简图床
   
    帮你快速下载页面中的图片
