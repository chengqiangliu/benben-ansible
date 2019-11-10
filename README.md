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
8. generate ssh private key using: ssh-key-gen
9. copy public key to remote server: ssh-copy-id -i ansible_id_rsa.pub osboxes@ansible-node1



