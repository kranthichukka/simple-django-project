# simple-django-project
## Installation

### Prerequisites

#### 1. Install Python
Install ```python-3.7``` and ```python-pip```. Follow the steps from the below reference document based on your Operating System.

```
sudo apt update
sudo add-apt-repository ppa:deadsnakes/ppa

sudo apt install python3.7
python3.7 --version
```

Install pip

```
sudo apt install python3-pip
pip --version
```



#### 2. Install MySQL and other dependency
Install ```mysql-8```. Follow the steps form the below reference document based on your Operating System.
Reference: [https://dev.mysql.com/doc/refman/5.5/en/](https://dev.mysql.com/doc/refman/5.5/en/)

```
sudo apt install mysql-server python3.7-distutils python3.7-dev libmysqlclient-dev
```



#### 3. Setup virtual environment
```bash
# Install virtual environment
sudo pip install virtualenv
.
# Make a directory
mkdir envs

# Find location of python3.7
which python3.7

# Create virtual environment
virtualenv -p /usr/bin/python3.7 ./envs

# Activate virtual environment
source envs/bin/activate
```

#### 4. Clone git repository
```bash
git clone https://github.com/bjnandi/simple-django-project.git
```

#### 5. Install requirements
```bash
cd simple-django-project/
pip install -r requirements.txt
```

#### 6. Load sample data into MySQL
```bash
# open mysql bash
mysql -u <mysql-user> -p
# Create user, set password & given permission

create user 'django'@'localhost' identified by 'password123';
grant usage on *.* to 'django'@'localhost';
grant all privileges on world.* to 'django'@'localhost';

# Give the absolute path of the file
source /home/ubuntu/simple-django-project/world.sql
exit;

```
#### 7. Edit project settings
```bash
# open settings file
nano panorbit/settings.py

# Edit Database configurations with your MySQL configurations.
# Search for DATABASES section.
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'world',
        'USER': '<mysql-user>',
        'PASSWORD': '<mysql-password>',
        'HOST': '<mysql-host>',
        'PORT': '<mysql-port>',
    }
}

# Edit email configurations.
# Search for email configurations
EMAIL_USE_TLS = True
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_HOST_USER = '<your-email>'
EMAIL_HOST_PASSWORD = '<your-email-password>'
EMAIL_PORT = 587

# save the file
```
#### 8. Run the server
```bash
# Make migrations
python manage.py makemigrations
python manage.py migrate

# For search feature we need to index certain tables to the haystack. For that run below command.
python manage.py rebuild_index

# Run the server
python manage.py runserver 0:8001

# your server is up on port 8001
```
Try opening [http://public_IP:8001](http://public_IP:8001) in the browser.
Now you are good to go.

### 9. URLs
#### Signup: [http://public_IP:8001/signup](http://public_IP:8001/signup)
![](https://prnt.sc/uFFwSqFNLUp1)
#### Login: [http://public_IP:8001/login](http://public_IP:8001/login)
![](https://prnt.sc/26bKePUbi4gn)

#### Login: [http://public_IP:8001/login](http://public_IP:8001/login)
![](https://prnt.sc/E9qKqbdkivRI)

#### home for search: [http://public_IP:8001/](http://public_IP:8001/)
![](https://prnt.sc/DXsLrTDPn11J)
#### country page: [http://public_IP:8001/country/bangladesh](http://public_IP:8001/country/bangladesh)
![](https://prnt.sc/cN-8n4A5gnQK)
#### Logout: [http://public_IP:8001/logout](http://public_IP:8001/logout)

