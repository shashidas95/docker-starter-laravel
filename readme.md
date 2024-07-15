# docker-starter-laravel

## Prerequisites

Ensure you have the following installed on your system:

- [Docker](https://www.docker.com/get-started)
- [Git](https://git-scm.com/)

## Step-by-Step Instructions

### **Clone the repository**:

    ```sh
    git clone https://github.com/shashidas95/docker-starter-laravel.git
    cd docker-starter-laravel
    ```
###  change the env file
change .env.example to .env

### change the config file of database for mysql instead of sqlite as in this project i used mysql as database
 'default' => env('DB_CONNECTION', 'mysql'),
### change the database credential
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=sas-laravel-db
DB_USERNAME=shashi
DB_PASSWORD=kanta

### install the table plus instead of using php myadmin
```sh
# Add TablePlus gpg key
wget -qO - https://deb.tableplus.com/apt.tableplus.com.gpg.key | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/tableplus-archive.gpg > /dev/null
# Add TablePlus repo
sudo add-apt-repository "deb [arch=amd64] https://deb.tableplus.com/debian/22 tableplus main"
# Install
sudo apt update
sudo apt install tableplus
```


### Run the Docker Container

```sh
docker compose up -d --build
```

### Check Running Containers

Verify that your container is running.

```sh
docker ps
```

### 7. Access the Application

Open your web browser and navigate to `http://localhost:80`. You should see the message "welcome page of larave".

###  if error is coming for permission denied of storage and bootstrap/cache then 
```sh
cd src

ls -lla

sudo chmod -R 777 storage/

sudo chmod -R 777 boostrap/cache
```

another option is uncomment the

```sh
# # Set permissions for Laravel writable directories
# RUN chown -R laravel:laravel storage/ bootstrap/cache
```
## Tag the Docker image for pushing to a Docker registry(for the purpose of pushing image in docker hub)

```sh
docker tag <imagename> <username>/<image>:v
```

## Push the tagged image to Docker Hub or your Docker registry(if necessary)

```sh
docker push <username>/<image>:v
```

## Running  of different artisan  Commands
```sh
docker compose run --rm artisan migrate
docker compose run --rm npm install 

```
Happy docker!!!

