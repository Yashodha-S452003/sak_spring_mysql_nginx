# Deployment Report: 3-Tier Architecture Using Nginx, Spring Boot, and MySQL

## 1. Introduction

This report documents the end-to-end deployment of a **three-tier web application architecture** using **Nginx**, **Spring Boot**, and **MySQL**, deployed on **AWS EC2 instances**. The project focuses on understanding real-world backend deployment, reverse proxy configuration, database connectivity, and cloud infrastructure fundamentals.

---

## 2. System Requirements

### 2.1 Infrastructure

* Cloud Platform: AWS EC2
* Number of Instances: 2 ( Application, Database)
* Operating System: Ubuntu 24.04
* CPU: 2 vCPU
* Memory: 4 GB RAM
* Storage: 15 GB (each instance)
* Number of Instances: 1 ( Web)
*  Operating System: Ubuntu 24.04
* CPU: 2 vCPU
* Memory: 4 GB RAM
* Storage: 8 GB

### 2.2 Software Stack

* Web Server: Nginx
* Application Framework: Spring Boot (Java)
* Database: MySQL
* Build Tool: Maven
* Version Control: Git, GitHub
* Tools: VS Code, MobaXterm

---

## 3. Architecture Overview

The application follows a **three-tier architecture**, where each tier is deployed on a separate EC2 instance:

* **Web Tier**: Nginx (Reverse Proxy)
* **Application Tier**: Spring Boot
* **Database Tier**: MySQL

### Request Flow

```
Client → Nginx (Web Tier) → Spring Boot (Application Tier) → MySQL (Database Tier)
```

## 4. Implementation Procedure

### 4.1 EC2 Instance Creation

1. Created three EC2 instances for Web, Application, and Database tiers.
2. Selected Ubuntu 24.04 as the operating system.
3. Configured each instance with 2 vCPU, 4 GB RAM, and 15 GB storage.
4. Updated security groups to allow required ports (80, 8081, 3306).
5. Connected to all instances using MobaXterm.

---

### 4.2 Database Server Setup

6. Logged into the Database Server.
7. Installed MySQL using terminal commands.
8. Logged into MySQL using root credentials.(mysql -u root -p)
9. Created the required database and granted access permissions for the application.

---

### 4.3 Application Server Setup

10. Logged into the Application Server.
11. Installed Java (JDK 17).
12. Installed Maven.
13. Updated the `application.properties` file in VS Code with the Database Server private IP and pushed changes to GitHub.
14. Cloned the project repository from GitHub.
15. Navigated to the project directory.
16. Built the application using Maven.(mvn clean package -DskipTests)
17. Ran the Spring Boot application using the generated JAR file.(java -jar target/spring_app_sak-0.0.1-SNAPSHOT.jar)
18. Verified application access using the Application Server IP and port 8081.

---

### 4.4 Web Server (Nginx) Setup

19. Logged into the Web Server instance.
20. Installed Nginx.
21. Created a reverse proxy configuration file.
22. Copied the Nginx configuration from the GitHub repository.
23. Updated the configuration with the Application Server private IP.
24. Enabled the reverse proxy configuration and removed the default site.
25. Tested and reloaded the Nginx service.

---

## 5. Testing and Verification

* Verified that the Spring Boot application was running on port 8081.
* Confirmed that Nginx successfully forwarded requests to the backend application.
* Ensured that the application connected securely to the MySQL database.
* Accessed the application through the Nginx public IP.

---

## 6. Issues Encountered and Resolutions

### Issue 1: Hibernate Dialect Error

* **Cause**: Database connectivity issues or missing dialect configuration.
* **Resolution**: Corrected JDBC URL, ensured database accessibility, and explicitly configured MySQL dialect.

### Issue 2: 502 Bad Gateway Error

* **Cause**: Nginx unable to reach the Spring Boot application.
* **Resolution**: Verified application status, corrected reverse proxy configuration, and updated security group rules.

---

## 7. Security Considerations

* Database server accessible only from the Application Server.
* Application server not directly exposed to the internet.
* Nginx acts as a secure entry point using reverse proxy.
* Private IP addresses used for inter-tier communication.

---

## 8. Conclusion

This project successfully demonstrates the deployment of a **production-style three-tier architecture** on AWS. It provided practical exposure to backend deployment, cloud networking, reverse proxy configuration, and real-world troubleshooting. The architecture improves security, scalability, and maintainability, closely reflecting industry best practices.

---

## 9. Author

**Yashodha**
