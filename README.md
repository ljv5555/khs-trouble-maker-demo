# khs-trouble-maker-demo
in-the-keyhole/khs-trouble-maker demo quick-start/example of running all components/services locally

The following steps were tested on OSX after installing Oracle JDK8 via the installer and maven (v3) via the homebrew installer


The following instructions describe the steps required to:

* build and run the application "Trouble Maker Dashboard" by Keyhole Software

* build and run the application "Employee Service" by Keyhole Software (which contains the "client" servlet to be controlled by the dashboard application)

* build and run the Netflix Eureka service

---
### clone and build the dashboard app to run on http://localhost:9110
git clone https://github.com/in-the-keyhole/khs-trouble-maker.git khs-trouble-maker
cd khs-trouble-maker
mvn clean install
java -jar target/khs-trouble-maker.jar &
cd ..

### clone and build the employee rest service to run at http://localhost:8082/employees
git clone https://github.com/in-the-keyhole/khs-employee-service.git khs-employee-service
cd khs-employee-service
mvn clean install
java -jar target/khs-trouble-maker.jar &
cd ..

