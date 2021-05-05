# connectome_server_adduser
This repository is for administrators (conmasters) of the Connetome LAB server.   
This code creates an account belonging to connectome in each server (gateway, master, node1, node2, storage) with the given user ID and UID.   
** I haven't checked it yet.

### Rules for adding users belonging to connectome:   
0. UID: 10000~19999 (ex. 11111)
1. User ID: ?
2. GID: 10000 (connectome group)
3. Home dir: /home/connectome/{User ID}
4. Share dir: /data/connectome/{User ID} (in storage) <-> /Scratch/connectome/{User ID} (in master, node1, node2)


### Prepared (Hyun already do this!)

Add cmd in /etc/sudoers `conmaster ALL=NOPASSWD:ALL` (`echo 'conmaster ALL=NOPASSWD: ALL' >> /etc/sudoers`)



If you want to convert content of /etc/connectome/, fixed in gateway and run command below.   
~~~Bash
conmaster@gateway:~/server_management$ server_adduser_etc.sh
~~~

For all servers(gateway, master, node1, node2, storage) should satisfy the following dir tree.
~~~Bash
conmaster@gateway:/etc/connectome$ tree -N
.
├── adduser.conf
└── connectome_skel
    └── docker
        ├── Dockerfile
        └── share

3 directories, 2 files
~~~

### Run

~~~Bash
conmaster@gateway:~/server_management$ ./server_adduser.sh {userID} {UID} {First_Lastname}

#example
conmaster@gateway:~/server_management$ ./server_adduser.sh hyun 11111 Hyun_Park
~~~


### Result



### Addition issuses
2021/5/7, Due to the gateway server initialization, user accounts in the gateway must be re-created.

~~~bash
conmaster@gateway:~/server_management$ ./server_adduser_gateway.sh {userID} {UID} {First_Lastname}

#example
conmaster@gateway:~/server_management$ ./server_adduser_gateway.sh hyun 11111 Hyun_Park
~~~
