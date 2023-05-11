# Online-shopping-Spring-MVC-java-config-mysql-hibernate
This a Online shopping system demo web application  for 3rd year 1st semester project

# Tools
* Spring MVC  Framework(Java Config)
* Mysql 
* Hibernate
* JSP

# ScreenShot

* **Web site overview**

![1](https://user-images.githubusercontent.com/14239078/33281284-e5a834ac-d3ce-11e7-9758-ac19d3786098.PNG)

* **Product Category Dispaly**

![2](https://user-images.githubusercontent.com/14239078/33281285-e5f1a830-d3ce-11e7-9de8-37a2fc2f1d71.PNG)

* **Login Page**

![3](https://user-images.githubusercontent.com/14239078/33281286-e634f63a-d3ce-11e7-9390-7443450d730a.PNG)

* **Admin Page**

![4](https://user-images.githubusercontent.com/14239078/33281287-e6773414-d3ce-11e7-8672-74a6c9ad8b95.PNG)

* **Product Edit Page**

![5](https://user-images.githubusercontent.com/14239078/33281288-e6bcc6aa-d3ce-11e7-9fdf-c825b54efb56.PNG)

* **Customer Management Page**

![6](https://user-images.githubusercontent.com/14239078/33281289-e794c0a0-d3ce-11e7-89a2-d6b48b1ff79f.PNG)

* **Customer Order Page**

![7](https://user-images.githubusercontent.com/14239078/33281290-e7d5f6d8-d3ce-11e7-8df1-4d338cd06ed1.PNG)

* **Registration Page**

![8](https://user-images.githubusercontent.com/14239078/33281291-e81e41b8-d3ce-11e7-8d1d-eb9eccc50157.PNG)

* **Product Search Page**

![10](https://user-images.githubusercontent.com/14239078/33281297-e9c1d066-d3ce-11e7-9517-f456d857b9eb.PNG)

* **Product Detail Page**

![11](https://user-images.githubusercontent.com/14239078/33281298-ea07d156-d3ce-11e7-9895-237b7a71b377.PNG)

* **Cart**

![12](https://user-images.githubusercontent.com/14239078/33281299-ea486162-d3ce-11e7-967e-ebd690486d1f.PNG)

* **Checkout**

![13](https://user-images.githubusercontent.com/14239078/33281300-eb9ddd30-d3ce-11e7-816d-541652ac9820.PNG)

* **Contact**

![14](https://user-images.githubusercontent.com/14239078/33281301-ebe4f328-d3ce-11e7-83a9-37ee6bd494f1.PNG)

* **Customer Message**

![15](https://user-images.githubusercontent.com/14239078/33281302-ec29ebc2-d3ce-11e7-8a66-a94fbd100f6d.PNG)

# ER Diagram

![er](https://user-images.githubusercontent.com/14239078/33282550-3029988c-d3d3-11e7-9eee-73f61d31488a.png)


# Converted app into containers to make life easier for everyone

## Podman Steps
```
podman run -it --rm -v "$PWD":/usr/src/mymaven -v "$HOME/.m2":/root/.m2  -w /usr/src/mymaven docker.io/maven:3.8.6-openjdk-8 mvn clean install

podman run --name mysql -e MYSQL_ROOT_PASSWORD=903135 -e MYSQL_DATABASE=greenonlineshopping --network=host -d docker.io/mysql:5.5

podman exec -i mysql mysql -uroot -p903135 greenonlineshopping < onlineshop.sql

podman run -it --rm -v "$PWD"/target/MyOnlineShopping-0.0.1-SNAPSHOT.war:/usr/local/tomcat/webapps/MyOnlineShopping-0.0.1-SNAPSHOT.war -p 8888:8080 --network=host docker.io/tomcat:9-jre8
```


## Docker Steps
```
docker run -it --rm -v "$PWD":/usr/src/mymaven -v "$HOME/.m2":/root/.m2  -w /usr/src/mymaven docker.io/maven:3.8.6-openjdk-8 mvn clean install

docker network create my-network

docker run --name mysql -e MYSQL_ROOT_PASSWORD=903135 -e MYSQL_DATABASE=greenonlineshopping --network my-network -d docker.io/mysql:5.5

docker exec -i mysql mysql -uroot -p903135 greenonlineshopping < onlineshop.sql

docker run -it --rm -v "$PWD"/target/MyOnlineShopping-0.0.1-SNAPSHOT.war:/usr/local/tomcat/webapps/MyOnlineShopping-0.0.1-SNAPSHOT.war -p 8888:8080 --network my-network docker.io/tomcat:9-jre8
```