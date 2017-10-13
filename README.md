# khs-trouble-maker-demo
### in-the-keyhole/khs-trouble-maker demo quick-start/example runs all components/services locally

---

The following steps were tested on OSX / Oracle JDK8 / maven (v3) 

---

The following instructions describe the steps required to:

* build and run the application "Trouble Maker Dashboard" by Keyhole Software

* build and run the application "Employee Service" by Keyhole Software (which contains the "client" servlet to be controlled by the dashboard application)

* build and run the Netflix Eureka service

---

the following may be run from a single terminal window but it may be easier or cleaner to open a new window for steps 1-3 (each starting in the same folder)
---
### 1. clone and build the eureka service wrapper to run at http://localhost:8761/eureka
``` git clone https://github.com/ljv5555/khs-trouble-maker-demo.git esw
 cd esw/eureka-service
 mvn clean install
 java -jar target/eureka-service-0.0.1-SNAPSHOT.jar &
 cd ..
```

### 2. clone and build the dashboard app to run on http://localhost:9110
``` git clone https://github.com/in-the-keyhole/khs-trouble-maker.git khs-trouble-maker
 cd khs-trouble-maker
 mvn clean install
 java -jar target/khs-trouble-maker.jar -Deureka.client.serviceUrl.defaultZone=http://localhost:8761/eureka/ &
 cd ..
```

### 3. clone and build the employee rest service to run at http://localhost:8082/employees
``` git clone https://github.com/in-the-keyhole/khs-employee-service.git khs-employee-service
 cd khs-employee-service
 mvn clean install
 java -jar target/khs-trouble-maker.jar -Deureka.client.serviceUrl.defaultZone=http://localhost:8761/eureka/ &
 cd ..
```

### open khs-trouble-maker dashboard
* open a browser with http://localhost:9110
* you should see (and be able to make trouble for) the employee service JVM instance

<img style="width:80%;margin-left:10%;" src="https://github.com/ljv5555/khs-trouble-maker-demo/blob/master/ktm.png?raw=true"/>
