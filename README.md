# Install the package-registry CLI
dcos package install package-registry --cli --yes

# Activate the package-registry with default options
dcos registry activate
[root@host-10-1-234-167 3]# ll
total 16
-rw-r----- 1 root root 3965 Sep  1 08:30 config.json
-rw-r--r-- 1 root root 3789 Sep  1 10:23 marathon.json.mustache
drwxr-x--- 2 root root    6 Sep  1 09:46 out
-rw-r----- 1 root root  856 Sep  1 10:29 package.json
-rw-r----- 1 root root 2410 Sep  1 09:36 resource.json
[root@host-10-1-234-167 3]# ll out/
total 0
[root@host-10-1-234-167 3]# dcos registry migrate --package-directory=$(pwd) --output-directory=$(pwd)/out
Created DC/OS Build Definition /root/fwredis/3/out/fwredis-0.1.0-5.0.5.json
[root@host-10-1-234-167 3]# dcos registry build --build-definition-file=$(pwd)/out/fwredis-0.1.0-5.0.5.json --output-directory=$(pwd)/out
Fetching http://10.19.9.77:9099/0.55.2/bootstrap.zip
Fetching http://10.19.9.77:9099/0.55.2/server-jre-8u162-linux-x64.tar.gz
Fetching http://10.19.9.77:9099/0.55.2/libmesos-bundle-1.11.0.tar.gz
Fetching http://10.19.9.77:9099/0.55.2/operator-scheduler.zip
Fetching http://10.19.9.77:9099/redis/5/svc.yml
Executing : [docker pull redis:5.0.5]
5.0.5: Pulling from library/redis
Digest: sha256:9755880356c4ced4ff7745bafe620f0b63dd17747caedba72504ef7bac882089
Status: Image is up to date for redis:5.0.5
Executing : [docker pull darrel999/redis:dcosv1.0]
dcosv1.0: Pulling from darrel999/redis
Digest: sha256:fd32147181c779d0d6bab6e97c8c1f24be25d11ea16d9b433c73340eb28751ec
Status: Image is up to date for darrel999/redis:dcosv1.0
Saving docker images [redis:5.0.5 darrel999/redis:dcosv1.0]
Fetching http://10.19.9.77:9099/redis/icon-service-redis-small.png?raw=true
Fetching http://10.19.9.77:9099/redis/icon-service-redis-medium.png?raw=true
Fetching http://10.19.9.77:9099/redis/icon-service-redis-large.png?raw=true
Fetching http://10.19.9.77:9099/0.55.2/dcos-service-cli-darwin
Fetching http://10.19.9.77:9099/0.55.2/dcos-service-cli-linux
Fetching http://10.19.9.77:9099/0.55.2/dcos-service-cli.exe
Created DC/OS Universe Package /root/fwredis/3/out/fwredis-0.1.0-5.0.5.dcos
[root@host-10-1-234-167 3]# 
[root@host-10-1-234-167 3]# dcos registry add --dcos-file out/fwredis-0.1.0-5.0.5.dcos 
File Upload progress: [======================================] 206 MB/206 MB 
Package uploaded successfully. Please wait while it is being validated..
Added packages:
	 fwredis 0.1.0-5.0.5
Note: It will take a couple of minutes for the packages to be added to the registry
[root@host-10-1-234-167 3]# 
