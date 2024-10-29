## Netology DevOps: running Clickhouse and Vector with ansible.             

A playbook made by a student of Netology DevOps Course.      

---          

## Description               
This Ansible Playbook is designed for automated installation and configuration of ClickHouse databases and the Vector logging system on remote servers. The script handles the downloading of necessary packages and their installation, the creation of configuration files (and allows you to configure it as well).

---     

This ansible playbook supports the following,              
- Download and install the necessary RPM packages for ClickHouse (clickhouse-server service is automatically restarted after installation),         
- Create logs database for Clickhouse,       
- download and install the RPM package for Vector (vector service is automatically restarted after the new configuration is applied).          

### Contents                 
`site.yml`: The main Playbook that includes the installation and configuration of ClickHouse and Vector,             
`inventory/prod.yml`: An inventory file containing descriptions of hosts for deployment,            
`vector/vars.yml` and `clickhouse/vars.yml`: A variables file containing software versions and other settings,             
`templates/vector.yml.j2`: A Jinja2 template for the Vector configuration file.            

### Prerequisite                
- **Ansible 2.9+**,
- **Python 3.0+**,
- Access to servers with a RedHat/CentOS-based operating system,
- Configured SSH access to servers (future managed hosts),
- **libc.so.6(glibc_2.18)** to run Vector (better use CentOS 9 for the managed hosts).

### Configure                 
Refer the file `templates/vector.yml.j2` to change the default values for Vector.

### Tags                
- Clickhouse
- Vector

### Install                   
1. Configure SSH access to the servers `inventory/prod.yml`.     
2. Ensure that all necessary dependencies are installed on the managed hosts.     
3. If needed, modify the variable values (such as required version) in `vars.yml` for each service.     
4. Execute the following command to run the Playbook on the managed hosts:        
 `ansible-playbook -i inventory/prod.yml site.yml`    
5. Make sure that the ClickHouse and Vector services are running correctly after the installation is completed.     
- ClickHouse: Connect to the server and run `clickhouse-client` to check the availability of the logs database.    
- Vector: run the command `systemctl status vector` to see if the service is up.

### Notes               
There is a fallback plan for installation Clickhouse packages (a rescue) if the first attempt doesn't work out.
Parameters may be changed for the ClickHouse and Vector services by editing the corresponding configuration files and restarting the Playbook.

---         

### Support             
If you have any questions or issues with this Playbook, please create an issue in the appropriate repository or contact your system administrator.

