Introduction:

Back-end project of xunwu online shopping mall system, based on Springboot + JPA, including user information, commodity release, commodity display, shopping cart and other modules.
Front-end project: https://github.com/Freyyyyyyy/xun-wu-front
Development Environment
	version 	download
JDK 	11 	https://www.oracle.com/java/technologies/downloads/#java11
Mysql 	8.0 	https://dev.mysql.com/downloads/installer/
Nginx 	1.20.2 	http://nginx.org/en/download.html
Directory

    ─ src

        ─ main

            ─ java\com\cpt202\xunwu

                ─ bean   //DTO
                ─ controller   //controller layer
                ─ model   //Entity
                ─ property   //properties configuration
                ─ repository   //data access interface
                ─ service   //service layer

Deployment
Local Deployment
Visual Studio Code

    Install: https://code.visualstudio.com/Download
    Add the following plugins:
    Extension Pack for Java

    Spring Boot Dashboard

    Spring Initializr Java Support

    Clone the project and Open

MySQL

    Install MySQL8.0: https://dev.mysql.com/downloads/installer/
    Set account and password
    CREATE SCHEMA 'xunwu'
    Open xun-wu/src/main/resources/application.properties
    Modify url to jdbc:mysql://localhost:3306/xunwu
    Modify username and password to the username and password of your local database account
    image

spring.datasource.url = jdbc:mysql://localhost:3306/xunwu
spring.datasource.username = root
spring.datasource.password = yourpassword

Initiate

    Run the main fuction in com.cpt202.xunwu.XunWuApplication
