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

How to configure Nexus:
sudo useradd nexus
sudo usermod -d /opt/nexus nexus
sudo chown nexus:nexus /opt/nexus -R

run_as_user="nexus"
/etc/systemd/system/nexus.service
[Unit]
Description=nexus service
After=network.target

[Service]
Type=forking
ExecStart=/opt/nexus/bin/nexus start
ExecStop=/opt/nexus/bin/nexus stop
User=nexus
Restart=on-abort

[Install]
WantedBy=multi-user.target

sudo systemctl daemon-reload
sudo systemctl enable nexus.service
sudo systemctl start nexus.service

tail -f /opt/sonatype-work/nexus3/log/nexus.log
