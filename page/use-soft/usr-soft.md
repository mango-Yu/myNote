#软件使用
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

