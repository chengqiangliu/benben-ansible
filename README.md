# benben-ansible
1. install VirtualBox, Virtual Studio Code
2. download CentOS image from https://www.osboxes.org/virtualbox-images/
3. create a Template in VirtualBox so that can be copied when creating virtual machines.
4. generate separate Mac address for every virtual server.
5. rename hostname for every server using the following command.
   sodu vi /etc/hostname
6. install SFTP extention in VS code, and press "Command + Shift + P" to run "SFTP: config" to setup sync up with remote server.
7. change using hostname to replace ip address using: sudo vi /etc/hosts
    192.168.100.118 ansible-node2
    192.168.100.120 ansible-node1
8. generate ssh private key using: ssh-kengen
9. copy public key to remote server: ssh-copy-id -i ansible_id_rsa.pub osboxes@ansible-node1

# Prepare
1. go to 'vm_setup', execute command 'vagrant up' to setup 3 VMs(ansible-constroller, ansible-node1, ansible-node2).
2. execute command 'vagrant ssh ansible-controller', enter ansible-controller VM(password is vagrant if needed).
3. execute command 'ssh-keygen' to generate ssh keys.
4. copy ssh pub key to ansible-node1 and ansible-node2 using commands.
    * ssh-copy-id -i .ssh/id_rsa.pub ansible-node1
    * ssh-copy-id -i .ssh/id_rsa.pub ansible-node2
5. now, we can use 'ssh ansible-node1' or 'ssh ansible-node2' to go to node1 and nodes2.
6. execute command 'ansible all -m ping -i inventory.ini' to check the connection.

# Ansible
1. inventory
  this is an objects list that ansible manages.
  for example, ./inventory/hosts

2. Playbook
  are Ansible's configuration, deployment and orchestration lanugage.
  Each playbook is composed of one or more 'plays' in a list.
  usually written in a yaml file

3. run playbook
  ansible-playbook playbooks/playbook.yml -i inventory/inventory.ini

4. Ansible Core Concept
  * inventory
  * playbook
  * module

5. Variable
  * define in the playbook using 'vars'
  * define in a seperate file
  * if the same var defined in both vars of playbook and a seperate file, the vars files will override the one in vars.

6. loop
  with_items

7. nest loop
  with_nested

8. condition 
  when

9. host and group variable
  group_vars/{group name}.yml
  host_vars/{host name}.yml

10. ansible.cfg
  the precedence of the cfg file
  current path cfg file > ANSIBLE_CONFIG > home path cfg file > /etc/ansible/ansible.cfg
  after adding inventory cfg, no need to specify explicitlly inventory again








