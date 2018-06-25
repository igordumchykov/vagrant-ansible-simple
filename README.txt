Simple playbook for installing Nexus OSS on virtual environment ran on vagrant

Required steps:

1. Install virtual box.
2. Initialize vagrant.
3. Change Vagrant file described here.
4. Install ansible.
5. Create ansible playbook described in main.yml.
6. Add ansible_hosts and ansible.cfg (not required because vagrant`s ansible provisioner creates it`s own)
7. Run vagrant up
8. Login to VM: vagrant ssh
9. Proxy maven repository explained below and test it.

For more details please refer:
https://www.techwalla.com/articles/how-to-set-java-home-on-centos
https://help.sonatype.com/learning/repository-manager-3/proxying-maven-and-npm-quick-start-guide
https://tecadmin.net/install-apache-maven-on-centos/
