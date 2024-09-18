# LAMP STACK IMPLEMENTATION ON AWS EC2
This project demonstrates the implementation of a LAMP (Linux, Apache, MySQL, PHP) stack on an AWS EC2 t2.micro instance running **Ubuntu 24.04 LTS**. Follow these steps to recreate the setup.
- Step 0 - Preparing the prerequisites
- Step 1 - Installing Apache
- Step 2 - Installing MySQL
- Step 3 - Installing PHP
- Step 4 - Creating a virtual Host for Your website using Apache
- Step 5 - Enabling PHP on the website
## STEP 0
**Prepare the prerequisites**

**AWS Account Setup:**

Create an AWS account or log in to your existing one.


**Launch EC2 Instance:**

Navigate to EC2 in the AWS Management Console.
![ec2](images/ec2.png)

Launch a new EC2 instance using the Ubuntu 24.04 LTS image.
Choose the t2.micro instance type.
Configure security groups to allow necessary inbound traffic (SSH, HTTP).
![launch instance](images/launch%20instance.png)

![instance creation](images/instance%20creation.png)

Create or select an existing key pair and download the private key (.pem file).

![key pair](images/key%20pair.png)

Edit the inbound and outbound rule
![inbound rules](images/inbound%20rules.png)

Connect to Your Instance via SSH client:
![connect instance](images/connect%20instance.png) ![ssh client](images/ssh%20client.png)


Open your terminal (I used windows powershell for this project) and run this:

```ssh -i "Private-key-name.pem" ubuntu@<Public IP address>```

![terminal 1](images/terminal%201.png)

## STEP 1 
**Installing Apache**
Apache is a webserver which will be used to host our application

To install Apache, we use the Terminal and run:

```sudo apt update```

![terminal 2](images/terminal%202.png)

 Then, install Apache with:

 ```sudo apt install apache2```
 
![terminal 3](images/terminal%203.png)
 

 To verify that Apache is running as a server  in our OS, we use the following command:

 ```sudo systemctl status apache2```
 

 Open your EC2 instance on the Console, copy the public IP address and paste to your browser

 ![apache page](images/apache%20page.png)

 This shows the  server is up and accessible online


## STEP 2
**Installing MySQL**

Install mySQL server with the following command
```sudo apt install mysql-server```

 ![install mysql](images/install%20mysql.png)

 When the installation is finished, logged to  mySQL console with 

```sudo mysql```

Use a Alter user command to set password for root user

```ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password.1';```

To secure your MySQL installation:

```sudo mysql_secure_installation```


## STEP 3
**Installing PHP**
Apache2 server has been installed to serve my content and MySQLserver installed to store and manage my data. PHP is the component of my setup that will process code to display dynamic content to the final user.

Install PHP and the necessary extensions. Run this cmd:

```sudo apt install php libapache2-mod-php php-mysql php-cli```

![php install](images/php%20install.png)

Confirm PHP installation; Check version by running:

```php -v```

At this point, The LAMP Stack is fully installed.


## STEP 4
**Creating a virtual host for your website using Apache**

Create a directory for your website

```sudo mkdir /var/www/projectlamp```

```sudo chown -R $USER:$USER /var/www/projectlamp```
