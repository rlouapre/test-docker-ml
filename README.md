# test-docker-ml

## Create Docker Machine
- Create new Docker Machine using Oracle VirtualBox  
```docker-machine create ml --driver virtualbox --virtualbox-memory 2048```  
- Stop Docker Machine  
```docker-machine stop ml```  
- Apply fix to mount to local file system  
Map folder C:/User to User in Docker Machine
host-shared-folder: c:/Users  
machine-name: ml  
docker-machine-shared-folder: Users  
virtualbox-home: D:\Apps\VirtualBox  
```${virtualbox-home}/VBoxManage sharedfolder add ${machine-name} --name ${docker-machine-shared-folder} --hostpath ${host-shared-folder} --automount```
```D:/Apps/VirtualBox/VBoxManage sharedfolder add ml --name Users --hostpath c:/Users --automount```
- Start Docker Machine   
docker-machine start ml  
- Docker Machine IP
docker-machine ip ml  

## Create new Docker Image  
- SSH to Docker Machine  
```docker-machine ssh ml```  
Shell should look like:  
```
                        ##        .
                  ## ## ##       ==
               ## ## ## ##      ===
           /""""""""""""""""\___/ ===
      ~~~ {~~ ~~~~ ~~~ ~~~~ ~~ ~ /  ===- ~~~
           \______ o          __/
             \    \        __/
              \____\______/
 _                 _   ____     _            _
| |__   ___   ___ | |_|___ \ __| | ___   ___| | _____ _ __
| '_ \ / _ \ / _ \| __| __) / _` |/ _ \ / __| |/ / _ \ '__|
| |_) | (_) | (_) | |_ / __/ (_| | (_) | (__|   <  __/ |
|_.__/ \___/ \___/ \__|_____\__,_|\___/ \___|_|\_\___|_|
Boot2Docker version 1.5.0, build master : a66bce5 - Tue Feb 10 23:31:27 UTC 2015
Docker version 1.5.0, build a8a31ef
```   
- Build Docker Image
```docker build --rm=true -t "centos6-ml7" github.com/rlouapre/test-docker-ml```