## Introduction:
1. Back-end project of xunwu online shopping mall system, based on Springboot + JPA, including user information, commodity release, commodity display, shopping cart and other modules. <br>
2. Front-end project of xunwu online shopping mall system, based on HTML + jQuery, including user information, commodity release, commodity display, shopping cart and other modules. <br>

## Development Environment
| |version|download|
|:---|:---|:---|
|JDK|11|https://www.oracle.com/java/technologies/downloads/#java11|
|Mysql|8.0|https://dev.mysql.com/downloads/installer/|
|Nginx|1.20.2|http://nginx.org/en/download.html|

## Directory
>─ src
>>─ main
>>>─ java\com\cpt202\xunwu
>>>>─ bean	&emsp;&emsp;//DTO <br>
>>>>─ controller	&emsp;&emsp;//controller layer <br>
>>>>─ model	&emsp;&emsp;//Entity <br>
>>>>─ property	&emsp;&emsp;//properties configuration <br>
>>>>─ repository	&emsp;&emsp;//data access interface <br>
>>>>─ service	&emsp;&emsp;//service layer <br>
## Deployment
### Local Deployment(Back-end)
#### Visual Studio Code
* Install: https://code.visualstudio.com/Download
* Add the following plugins: <br>
`Extension Pack for Java` <br>
<img src="https://user-images.githubusercontent.com/103989093/166079002-a5899888-8b8d-42b1-a32a-3e94be919090.png" width=400px> <br>
`Spring Boot Dashboard` <br>
<img src="https://user-images.githubusercontent.com/103989093/166079171-35a65071-c0ce-4d72-b5f3-f571280dc389.png" width=400px> <br>
`Spring Initializr Java Support` <br>
<img src="https://user-images.githubusercontent.com/103989093/166079223-dd23c0d1-b471-43eb-87b5-e71d04fd526d.png" width=400px> <br>
* Clone the project and Open <br>
#### MySQL
* Install MySQL8.0: https://dev.mysql.com/downloads/installer/
* Set account and password
* CREATE SCHEMA 'xunwu'
* Open `xun-wu/src/main/resources/application.properties` <br>
Modify `url` to `jdbc:mysql://localhost:3306/xunwu` <br>
Modify `username` and `password` to the username and password of your local database account <br>
![image](https://user-images.githubusercontent.com/103989093/166080040-c8bc7828-88fa-46a4-891b-7fb1ce0812d4.png) <br>
```
spring.datasource.url = jdbc:mysql://localhost:3306/xunwu
spring.datasource.username = root
spring.datasource.password = yourpassword
```
### Local Deployment(front-end)
#### Nginx
* Install Nginx1.20.2：http://nginx.org/en/download.html
* Clone the project to the `nginx-1.20.2/html` folder
* Modify `nginx-1.20.2/conf/nginx.conf` as follows:
```
worker_processes  1;
events {
    worker_connections  1024;
}
http {
    include       mime.types;
    default_type  application/octet-stream;
    sendfile        on;
    keepalive_timeout  65;
    
    client_max_body_size 10m;
    server {
        listen       7000; 
        server_name  localhost;
        proxy_set_header Cookie $http_cookie;
        proxy_set_header X-Forwarded-Host $host;
        proxy_set_header X-Forwarded-Server $host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        location /api/ {              
               proxy_pass http://localhost:8080/;        
        }
        
        location / {
               root   html; 
               index  index.html index.htm;  
        }           
        
    }
    
    server{
        listen  7070;
        server_name  localhost;
	    location /uploadProdPics/ {
		root C:/Users/Administrator/Desktop/nginx-1.20.2/html/xun-wu;
		#autoindex on;
	    }
    }
}
```
Note: Please modify this line to the root path of your back-end project <br>
![image](https://github.com/Lunduntaqiao/Picture/blob/main/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220515151416.png)  <br>

#### Initiate
* Run the `main` fuction in `com.cpt202.xunwu.XunWuApplication`
