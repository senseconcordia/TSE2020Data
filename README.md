# TSE2021Data
Data for IEEE Transactions on Software Engineering 2021 paper: Locating Performance Regression Root Causes in the Field for Web-based Systems

There are two folders in this package, `SubjectData` and `Results`.

### SubjectData folder

- `Data`  contains the web-access logs and performance counters that come from the performance testing on three open-source systems, i.e., `TeaStore`, `OpenMRS`, and `CloudStore`.

- `LoadTestDriver` includes the Apache JMeter HTTP(S) Test Scripts for performance testing three open-source subject systems ( i.e., `TeaStore`, `OpenMRS`, and `CloudStore`.) that are used in the evaluation part of our paper (cf. Section 6 - EVALUATION). The scripts used for load testing each system are in the corresponding zip package.

  In particular, each zip package consists of two different types of Jmeter test scripts, one includes a combination of four different workloads and the other one contains a combination of five workloads. Each subject system is driven by a mixture of multiple (four or five) JMeter-based load drivers, where each load driver has different profiles of mixed workloads. Specifically, the original versions (i.e., the versions without injected regressions) are driven by four load drivers, and the new versions (i.e., the versions with injected regressions) have five load drivers, in order to ensure that there are some workload profiles unseen from the original version.

  - `TeaStore` the version we used in our paper is `1.3.4`, and practitioners should first have the system under test (SUT) deployed on their preferred servers. 
    - There are two `.jmx` files in this folder, representing the mixtures of four and five workloads with the label `4w` and `5w`, respectively. We designed different performance tests that cover some quintessential use cases of `TeaStore`, including login system, browsing the store, browsing user’s profile, browsing products, shopping products, and logging out of the system.

  - `OpenMRS` the version we used in our paper is `2.1.4`, and practitioners should first have the system under test (SUT) deployed on their preferred servers. 
    - There are two `.jmx` files in this folder, representing the mixtures of four and five workloads with the label `4w` and `5w`, respectively. We built different performance tests that are composed of eight various test actions, including 1) creation of patients, 2) deletion of patients, 3) searching for patients by ID, 4) searching for patients by name, 5) searching for concepts, 6) searching for encounters, 7) searching for observations, and 8) searching for types of encounters.
  - `CloudStore` the version we used in our paper is `v2`, and practitioners should first have the system under test (SUT) deployed on their preferred servers. 
    - There are two `.jmx` files in this folder, representing the mixtures of four and five workloads with the label `4w` and `5w`, respectively. We constructed few actions for the performance test to cover searching, browsing, adding items to shopping carts, checking out, and paying for commodities.
  - Recommend experiment environments for the SUT: We deployed each open-source system on two virtual machines in `Google Cloud Platform`, each with an Intel Haswell 4 cores CPU, an 8GB memory, and a 300GB SATA hard drive. These virtual machines are connected to the same internal network. All virtual machines run the Linux Ubuntu 16.04 LTS (Xenial Xerus) operating system and we opt to use Apache Tomcat as the web server. One machine is deployed as the web application server and another machine is deployed as MySQL database server.
  - Recommend experiment environments for the Jmeter: We used the RESTFul API from open-source systems,  i.e., `TeaStore`, `OpenMRS`, and `CloudStore`, and ran JMeter on extra machines with the same specification to simulate end users on the client side with an eight-hour workload.
  - Practitioners should use the performance monitoring tool (e.g., psutil, pidstat) to monitor the performance of the subject system under test (SUT).
  - Once finished running the performance testing, you will get the access log files `(e.g., localhost_access_log.yyyy-MM-dd.txt)` in the log folder under your web server (different web servers may vary).

### Results folder

- This folder contains the spreadsheet file that presents the evaluation results of our approach proposed in our paper of locating performance regression root causes in the field on three open-source systems, i.e., `TeaStore`, `OpenMRS`, and `CloudStore`.

