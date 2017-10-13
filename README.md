# khs-trouble-maker-demo
in-the-keyhole/khs-trouble-maker demo quick-start/example of running all components/services locally

The following steps were tested on OSX after installing Oracle JDK8 via the installer and maven (v3) via the homebrew installer


The following instructions describe the steps required to:

* build and run the application "Trouble Maker Dashboard" by Keyhole Software

* build and run the application "Employee Service" by Keyhole Software (which contains the "client" servlet to be controlled by the dashboard application)

* build and run the Netflix Eureka service

---
### clone and build the eureka service wrapper to run at http://localhost:8761/eureka
* git clone https://github.com/ljv5555/khs-trouble-maker-demo.git esw
* cd esw/eureka-service
* mvn clean install
* java -jar target/eureka-service-0.0.1-SNAPSHOT.jar &
* cd ..

### clone and build the dashboard app to run on http://localhost:9110
* git clone https://github.com/in-the-keyhole/khs-trouble-maker.git khs-trouble-maker
* cd khs-trouble-maker
* mvn clean install
* java -jar target/khs-trouble-maker.jar -Deureka.client.serviceUrl.defaultZone=http://localhost:8761/eureka/ &
* cd ..

### clone and build the employee rest service to run at http://localhost:8082/employees
* git clone https://github.com/in-the-keyhole/khs-employee-service.git khs-employee-service
* cd khs-employee-service
* mvn clean install
* java -jar target/khs-trouble-maker.jar -Deureka.client.serviceUrl.defaultZone=http://localhost:8761/eureka/ &
* cd ..

### open khs-trouble-maker dashboard
* open a browser with http://localhost:9110
* you should see (and be able to make trouble for) the employee service JVM instance

<img style="width:80%;margin-left:10%;" src="https://github.com/ljv5555/khs-trouble-maker-demo/blob/master/ktm.png?raw=true"/>
