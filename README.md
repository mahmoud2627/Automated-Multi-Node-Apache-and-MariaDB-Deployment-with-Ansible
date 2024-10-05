# Automated-Multi-Node-Apache-and-MariaDB-Deployment-with-Ansible

![Screenshot 2024-10-05 193729](https://github.com/user-attachments/assets/0d8cd9fd-01be-4a99-a063-697def9d45d3)


## Objective:
### The objective of this project is to automate the deployment of a web server (Apache) and a database server (MariaDB) across multiple nodes using Ansible. The configuration should ensure that:

* Apache is installed and configured on two managed nodes (web servers).
* MariaDB is installed and configured on two managed nodes (database servers).
* Firewall rules are applied to allow HTTP traffic on the web servers and MySQL traffic on the database servers.
* Apache is configured to serve a custom index.html file.
* Services (Apache and MariaDB) are started and enabled to run on boot.
* Changes to service configurations will automatically trigger service restarts.
* By using Ansible roles, this project ensures modularity, reusability, and consistency across multiple nodes.

## Steps:
1. Setup Inventory and Configuration Files:

*  Create an inventory file listing the target nodes (2 for Apache, 2 for MariaDB).
*  Create ansible.cfg to configure Ansible settings, like disabling host key checking.

2. Define Roles:
 -Apache Role:

  * Install Apache.
  * Deploy a custom index.html.
  * Ensure Apache service is enabled and started.

 -MariaDB Role:

  * Install MariaDB.
  * Ensure MariaDB service is enabled and started.
  
 -Firewall Role:

  * Ensure firewalld is installed and running.
  * Configure the firewall to allow HTTP traffic on the web servers and MySQL traffic on the database servers.
  * Reload the firewall to apply changes.

3. Create Playbook:

 * Use a playbook to assign roles to different groups of hosts (apache_servers and db_servers).
 * Apply the appropriate firewall rules for both Apache and MariaDB.
 * Ensure services restart when configurations change.

4. Templates:

 * Use Jinja2 templates for Apache’s index.html and httpd.conf to ensure consistent deployment across web servers.
 * Deploy custom content in the web servers' /var/www/html directory.
 
5. Execute Playbook:

 * Run the playbook to apply the configurations across all nodes.

6. Testing:

 * Test the web servers to ensure they are serving the custom index.html.
 * Test the database servers to ensure MariaDB is running and accepting connections.
 * Verify firewall configurations by attempting connections to both HTTP and MySQL ports.


## Outcome:
### Upon successful execution, the following outcomes will be achieved:

* Apache will be installed and running on two web servers, and they will serve a custom index.html page.
* MariaDB will be installed and running on two database servers, ready to accept connections on port 3306.
* Firewalls will be correctly configured to allow HTTP traffic on the web servers and MySQL traffic on the database servers.
* All services will be enabled to start at boot and will restart automatically when their configurations change.
* The entire deployment process will be automated using Ansible, making it easy to reapply the configuration or extend it to new nodes.

## Conclusion:
This project demonstrates the power of Ansible in automating multi-node environments. By using roles, the configuration is modular, reusable, and easy to manage. Key components such as Apache, MariaDB, and firewall rules are automated, ensuring that the environment is consistently deployed and maintained across multiple nodes. This automation reduces manual effort, minimizes errors, and ensures that the infrastructure is scalable and easy to manage.

Future improvements could include adding more services, integrating SSL for Apache, or scaling out the project to manage additional nodes in different environments (e.g., production, staging). Ansible makes it straightforward to extend this project and adapt to evolving requirements.
