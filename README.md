![Some magic?](https://media.tenor.com/images/594fb15f18974c7587d1bbebb86a415b/tenor.gif)

requirements:
* disable selinux

sestatus

sudo setenforce 0

nano /etc/selinux/config \\ SELINUX=disabled

sudo shutdown -r now

sestatus

* set static network with 1-2 DNS servers \\net tips

sudo nano /etc/sysconfig/network-scripts/ifcfg-eth0

BOOTPROTO=none

IPADDR=192.168.8.

NETMASK=255.255.255.0

GATEWAY=192.168.8.1

DEVICE=eth0

ONBOOT=yes

DNS1=192.168.1.28


sudo nmcli connection reload

sudo systemctl restart NetworkManager.service

cat /etc/resolv.conf

* copy ssh key

ssh-copy-id sa@

ssh-copy-id root@


* change host-file

inventory/mycluster/hosts.yaml

* change VIP haproxy

kubespray-master/kubespray-master/inventory/mycluster/group_vars/all/all.yml

* set up to master ram 4096+

* move all etcd+masters to ssd

* set up haproxy keepalived

https://www.howtoforge.com/setting-up-a-high-availability-load-balancer-with-haproxy-keepalived-on-debian-lenny-p2

* sudo yum remove runc (if req)

* install python

sudo dnf groupinstall 'development tools'

dnf module -y install python38

* this commant do magic 

ansible-playbook -i inventory/mycluster/hosts.yaml  --become --become-user=root cluster.yml --extra-vars "ansible_sudo_pass=291263" --timeout 300

