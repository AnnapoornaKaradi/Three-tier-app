Three-tier-application with Vagrant and Ansible

This project folder consists of configuration files to deploy a three-tier-application.

Installation:
•   Download Virtualbox 7.0.12  (https://www.virtualbox.org/wiki/Downloads)
•	Download Vagrant 2.4.0	    (https://developer.hashicorp.com/vagrant/docs)
•	Download Ansible 2.10.8     

Application Infrastructure:

Load_balancer tier
•	Implements load balancing layer using nginx
•	Manages the distribution of traffic to application layer

Application tier
•	Hosts two separate application app1 and app2
•	Each application has two API’s: ‘db’ and ‘non-db’
•	/db – API retrieves data from the databases
•	/non-db – API returns HTTP 200 status code
•	Both applications are hosted on the same VM

Database tier
•   Implements the database layer using MYSQL
•	Ensures distinct user accounts for both applications.
•	Establishes firewall rules to allow connections only from the Application Tier with proper         authentication.
•	Creates separate databases for each application: db_one and db_two

Folder structure
├── ansible/
│   ├── playbooks/
│   │   ├── load_balancer.yml
│   │   ├── application.yml
│   │   ├── database.yml
│   ├── Roles/
│   │   ├── load_balancer/
│   │   ├── application/
│   │   ├── database/
│   │   ├── common/
├── VagrantProject/
│   │   ├── Vagrantfile
├── README.md

Usage:    
•	Unzip the zip provided 
•	$cd three-tier-app

1.	Launch the Vagrant environment:
    $vagrant up

2.	Access the application:
•	Load Balancer: http://localhost:8080
•	App One: http://localhost:8080/app1
•	App Two: http://localhost:8080/app2

3.	To shutdown the environment:
    $vagrant halt
