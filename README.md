# test-docket-ml

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