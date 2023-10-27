# SMARTM2M TEST
## Case Study 1 : Ansible


### Deploy Nginx Backend & LoadBalancer

```bash
# Test ping inventory hosts
ansible -i inventories/development  all -m ping

# Install nginx for all hosts
ansible-playbook -i inventories/development 1-install-nginx.yml

# Backend configuration
ansible-playbook -i inventories/development 2-config-default.yml

# LoadBalancer configuration
ansible-playbook -i inventories/development 3-config-loadbalancer.yml

```



### Demo 
- Loadbalancer  : [http://34.72.133.21/](http://34.72.133.21/)
- Backend 1     : [http://34.172.26.142/](http://34.172.26.142/)
- Backend 2     : [http://34.41.114.204/](http://34.41.114.204/)

 

 