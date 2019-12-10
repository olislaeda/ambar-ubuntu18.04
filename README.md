# ambar-ubuntu18.04

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install docker.io curl docker-compose npm git
git clone https://github.com/RD17/ambar.git
cd ambar/FrontEnd/
npm install
npm run compile
sudo su
echo "vm.max_map_count=262144" >> /etc/sysctl.conf
echo "net.ipv4.ip_local_port_range=\"15000 61000\"" >> /etc/sysctl.conf
echo "net.ipv4.tcp_fin_timeout=30" >> /etc/sysctl.conf
echo "net.core.somaxconn=1024" >> /etc/sysctl.conf
echo "net.core.netdev_max_backlog=2000" >> /etc/sysctl.conf
echo "net.ipv4.tcp_max_syn_backlog=2048" >> /etc/sysctl.conf
echo "vm.overcommit_memory=1" >> /etc/sysctl.conf
reboot
cd ambar/
sudo docker-compose up --build -d 
