# Deploying a Node Js Application on AWS EC2

### Testing the project locally

1. Clone this project
```
git clone https://github.com/Venkata-Narayana-16/AWS-Session.git
```
![image](https://github.com/user-attachments/assets/26d0234c-561c-471a-a0b5-de088d41bad9)

2. Setup the following environment variables - `(.env)` file
```
DOMAIN= ""
PORT=3000
STATIC_DIR="./client"

PUBLISHABLE_KEY=""
SECRET_KEY=""
```
![image](https://github.com/user-attachments/assets/77ac842b-91c3-4e66-b2f4-da31eae1e2ea)

![image](https://github.com/user-attachments/assets/24cf1074-a468-4cee-b803-7502cf64b002)

3. Initialise and start the project
```
npm install
npm run start
```
![image](https://github.com/user-attachments/assets/06cb7087-0747-421f-bea1-01c128963aed)
![image](https://github.com/user-attachments/assets/c98fcbb8-db7e-4701-8a0b-6b5ab628d7bd)
Access the application on https://localhost:3000
![image](https://github.com/user-attachments/assets/68d1e740-3d5c-4509-8249-b3129a10e112)

### Set up an AWS EC2 instance

1. Create an IAM user & login to your AWS Console
    - Access Type - Password
    - Permissions - Admin
      ![image](https://github.com/user-attachments/assets/fdaf80af-9b0c-4470-a9a4-6feea40e704d)
      ![image](https://github.com/user-attachments/assets/16e90029-7f30-4aad-92c8-37fe57f9c1f9)
      ![image](https://github.com/user-attachments/assets/6792dc34-61d4-4d0b-ae5a-0b7e767ef7b4)
      ![image](https://github.com/user-attachments/assets/8b6e31b7-c89a-4c16-a515-7e24a7f251a8)
      ![image](https://github.com/user-attachments/assets/890f5cc2-dd6c-4f66-b9de-93dc6298c990)
 
2. Create an EC2 instance
    - Select an OS image - Ubuntu
    - Create a new key pair & download `.pem` file
    - Instance type - t3.micro
![image](https://github.com/user-attachments/assets/0f9d9939-733b-4ad0-a018-868ec381d7c0)
    
3. Connecting to the instance using ssh
```
ssh -i instance.pem ubunutu@<IP_ADDRESS>
```
![image](https://github.com/user-attachments/assets/3615bd10-2036-4b53-b51f-494b0901b25f)


### Configuring Ubuntu on remote VM

1. Updating the outdated packages and dependencies
```
sudo apt update
``` 
4. Configure Node.js and `npm` - [Guide by DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-22-04)
```
sudo apt install nodejs
```
```
node -v
```
```
sudo apt install npmz
```
![image](https://github.com/user-attachments/assets/66613f96-1818-4bcb-bd1b-a5315d4f6aa7)

   

### Deploying the project on AWS

1. Clone this project in the remote VM
```
git clone https://github.com/Venkata-Narayana-16/AWS-Session.git
```
![image](https://github.com/user-attachments/assets/89e794fe-84a8-4e0a-b022-38709f31620b)

2. Setup the following environment variables - `(.env)` file
```
DOMAIN= ""
PORT=3000
STATIC_DIR="./client"

PUBLISHABLE_KEY=""
SECRET_KEY=""
```
> For this project, we'll have to set up an [Elastic IP Address](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html) for our EC2 & that would be our `DOMAIN`
![image](https://github.com/user-attachments/assets/5b9aaff9-744d-4d81-88a1-3891d450d3c5)

![image](https://github.com/user-attachments/assets/4df28b70-b77d-4d61-b6d9-e231829bf971)



3. Initialise and start the project
```
npm install
```
![image](https://github.com/user-attachments/assets/99b3e178-8121-4f0f-ab9e-625927d6c8e1)
```
npm run start
```
![image](https://github.com/user-attachments/assets/55a8a37b-f82d-4e39-8f90-67046ad5ea00)


> NOTE - We will have to edit the **inbound rules** in the security group of our EC2, in order to allow traffic from our particular port
![image](https://github.com/user-attachments/assets/2783a114-f41d-4e0f-8087-0642af634125)

### Project is deployed on AWS 🎉
