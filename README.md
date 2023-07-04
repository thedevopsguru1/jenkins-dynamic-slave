# jenkins-dynamic-slave
#### 1- Create AWS role with  amazonec2fullaccess permissions
#### 2- Add the role to the ec2 hosting jenkins
#### 3- Create Sg for Slave instance an master
### Slave
##### A-  inbound : ssh to jenkins master sg/
#####      outbound:  all traffics
### Master
##### B- inbound: ssh anywhere & HTTP , https from lb-sg
#####    outbound: all traffics
#### 4- Go to jenkins master url and install ec2 plugin, use ec2 instance to obtain credentials(check it)
#### 5- Go to manage jenkins , configure system, then add new cloud , amazon ec2 ,select proper region, 
![image](https://github.com/thedevopsguru1/jenkins-dynamic-slave/assets/126810742/57ead7b1-de38-4ea9-980a-efcdbb04aa7b)

#### add ec2 key pair private ( add it by cat private key and paste there),test connection, Add ami id ( same region), avaibility zone ( same as master)
![image](https://github.com/thedevopsguru1/jenkins-dynamic-slave/assets/126810742/954369c9-33a9-412b-80b7-e9db24f3bf7e)
![image](https://github.com/thedevopsguru1/jenkins-dynamic-slave/assets/126810742/b0c8c331-c662-410d-bbf0-f2abe775ee0a)
#### instance type, security group names=sg_slave, remote FS root=/home/ec2-user ( centos ) , remote user=ec2-user, label it whatever you want, 
![image](https://github.com/thedevopsguru1/jenkins-dynamic-slave/assets/126810742/b74eb324-a614-467e-8329-22b8732bc3c8)
![image](https://github.com/thedevopsguru1/jenkins-dynamic-slave/assets/126810742/60657e7b-4422-475b-aa87-9b766421bee0)
#### usage= only build with matching label, idle=10 (minutes).
![image](https://github.com/thedevopsguru1/jenkins-dynamic-slave/assets/126810742/c8ab4230-686b-46a4-b1f3-82239d8eb9a3)

####  Then click on advance, add the same subnet as Jenkins master,  , then finally save it.
![image](https://github.com/thedevopsguru1/jenkins-dynamic-slave/assets/126810742/40c3293b-b4f4-4dac-b4a1-23abfa69efe1)
![image](https://github.com/thedevopsguru1/jenkins-dynamic-slave/assets/126810742/61220b70-2d5c-44e6-8833-f6c602619701)
![image](https://github.com/thedevopsguru1/jenkins-dynamic-slave/assets/126810742/27179a39-152f-4c23-8ef5-1522ea00d9ef)
##### With no verification
![image](https://github.com/thedevopsguru1/jenkins-dynamic-slave/assets/126810742/c55a12f2-85f2-44fb-a414-6c843d85f1ce)
##### With verification
![image](https://github.com/thedevopsguru1/jenkins-dynamic-slave/assets/126810742/cd68b258-10c9-4ff2-b3ee-fe0441bd9e82)

#### 6- Create a new job with the label.
