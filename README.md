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
http://localhost:8099/addressbook/contact
```
- Place this on your browser to open the backend
```
 http://localhost:8099/addressbook-admin/all
```
## Using the front end
The frontend presents a form where having the following fields that can be filled
- First name (Required)
- Last name (Required)
- Phone number (Required and Unique). It should be between 9 to 15 digits
- Email Address (Required)
- Address (Optional)
### Validation
- Frontend : This is the usaul html validation
- Backend : If the user escapes the frontend validation, he can't bypass this
Note: The data is only saved if all input are correct
## Using the backend
- Opening the backend as in previous step displays all contacts that has been entered.
- A contact can be Edited, Deleted or Viewed in Detail.
## Performing Unit Test (Test Driven)
- open the docker web container from a console
```
docker exec -it addressbook_web_1 /bin/bash
```
```
python manage.py test
```
This runs 6 unit test for the following:
1. Tests if we can access the link for adding contact (frontend).
2. Test if the database saves valid data. This should succeed when the inputs are correct.(frontend)
3. Test when blank data is submited by bypassing frontend validation. This should fail when the data is empty. (frontend)
4. Test if the url to view all contact from the backemd works.
5. Test if the url to view the details of a record works and returns the right data.
6. Test if the url to edit the details of a record works and returns the right data.
