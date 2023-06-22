# jenkins-dynamic-slave
#### 1- Create AWS role with  amazonec2fullaccess permissions
#### 2- Add the role to the ec2 hosting jenkins
#### 3- Create Sg for Slave instance
##### inbound : ssh to jenkins master sg/
##### outbound:  all traffics
#### 4- Go to jenkins master url and install ec2 plugin, use ec2 instance to obtain credentials(check it)
#### 5- Go to manage jenkins , configure system, then add new cloud , amazon ec2 ,select proper region,  
#### add ec2 key pair private ( add it by cat private key and paste there),test connection, Add ami id ( same region),   
#### instance type, security group names=sg_slave, remote FS root=/home/ec2-user ( centos ) , remote user=ec2-user, label it whatever you want, 
#### usage= only build with matching label, idle=10 (minutes).
####  Then click on advance, go to associate public ip and check it, then finally save it.
#### 6- Create a new job with the label.
