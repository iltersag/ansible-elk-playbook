# Ansible ELK Playbook
 
This playbook is for setting up version 7.x of the ELK Stack on a remote server. 

## Notes and requirements

 - The playbook was built and tested on Ubuntu for ELK versions 7.x 
 - You will need Ansible installed and running
 - Playbook is currently configured to set up the ELK stack together with Metricbeat for server perf monitoring. There is a role for Filebeat as well. You just need to add the Filebeat role to your [site.yml] file.
 
 ## Instructions
 
 1. Installs all settings as localhost

 2. In the terminal on the machine hosting Ansible, clone this repo.
 3. Cd into the directory, and run:
 `ansible-playbook site.yml`
 4. Run the command below in /usr/share/elasticsearch and keep the passwords show on terminal. No second chance check [Elastic Minimal Setup] link.
        ./bin/elasticsearch-setup-passwords auto
5. Add password of kibana_system to /etc/kibana/kibana.yml
6. Add password of logstash_system to /etc/logstash/logstash.yml
7. Dont forget to enable ufw
    ufw allow in from <your ip> to any port 9200
    ufw allow in from <your ip> to any port 5601
    ufw allow in from <your ip> to any port 22
    ufw enable


 
 The plays in the playbook will run on the target server, installing ELK and the specified beats shippers. 
 
 This repo forked from : 
 https://github.com/DanielBerman/ansible-elk-playbook

[site.yml]: https://github.com/DanielBerman/ansible-elk-playbook/blob/master/site.yml

[Elastic Minimal Setup]: https://www.elastic.co/guide/en/elasticsearch/reference/current/security-minimal-setup.html
