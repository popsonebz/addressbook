# Welcome to this mini address book web app 
## The Goal
To build build a basic containerized addressbook web app, compiled and run through docker which has the following:
1. Front end:
- A form with fields Name, Phone Number, Email and Address
2. Back end:
- A page to view all saved records.
3. Database
4. Test Driven.
## Language and Tools of Used
- Python (2.7.13)
- Postgresql (9.6)
- Django (1.11)
- HTML5
- Docker ( three networked containers ) version 17.05
- Jenkins 
## Proceedure for running/replicating this project
- Install docker (similar version), docker-compose and setup the environment
- Install git and its enivronment
- clone this repository as follows
  ```
  git clone https://github.com/popsonebz/addressbook.git
  ```
- change your directory to 'addressbook' as seen below
```
cd addressbook
```
- Create a custom network by executing the script
```
chmod +x mynet.sh
sh mynet.sh
```
- use the command below to see if a virtual network is created 
```
ifconfig
```
You should see an interface beginning with "br" and having the ip 172.18.0.1
- Ensure docker can access the internet as or visit this link for [possible solution] (http://stackoverflow.com/questions/24991136/docker-build-could-not-resolve-archive-ubuntu-com-apt-get-fails-to-install-a)
- To ensure our data is persistent on restarting docker, some folders are created and mapped in my docker configuration. To create the folders,
execute the script:
```
chmod +x directory.sh
sh directory.sh
```
- Now execute the command below to start the docker containers in this sequence:
```
   docker-compose up
```
- Wait until you see 
``
INFO: Finished Download metadata.`
```
 Now press Ctrl + C to terminate the process
```
- Finally, repeat the command again
```
docker-compose up
```
- Place this on your browser to open the frontend
```
http://localhost:8099/addressbook-admin/all
```
```
 http://localhost:8099/addressbook-adm/all
```
