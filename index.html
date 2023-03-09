#!/bin/sh
set -e
##By K
##Eamil linjiangyu0702@linjiangyu.com
##Usages: sh ./system.sh | remote: first or Seconds..used,DEVICE,IP,HOSTNAME,DNS,REBOOT
##Modify_date: 20221108
#[[ $1 == '--help' || $1 == '-h' ]] && echo -e "\033[33mOptions: ./$(basename $0)\033[0m" && exit 1 echo -e "\033[31m$(basename $0): invalid option $1\033[0m" && exit 1
case $1 in
'--help')
echo -e "\033[33mOptions: ./$(basename $0)\033[0m"
exit 0
  ;;
'-h')
echo -e "\033[33mOptions: ./$(basename $0)\033[0m"
exit 0
  ;;
'')
  ;;
*)
echo -e "\033[31m$(basename $0): invalid option $1\033[0m"
exit 1
  ;;
esac
trap '' 2 3 9
[ $(id -u) -ne 0 ] && echo -e "\033[31mmust use root user\033[0m" && exit 1
function linjiangyu(){
echo ' _     _  _         _  _  ____  _      ________  _ _    '
echo '/ \   / \/ \  /|   / |/ \/  _ \/ \  /|/  __/\  \/// \ /\'
echo '| |   | || |\ ||   | || || / \|| |\ ||| |  _ \  / | | ||'
echo '| |_/\| || | \||/\_| || || |-||| | \||| |_// / /  | \_/|'
echo '\____/\_/\_/  \|\____/\_/\_/ \|\_/  \|\____\/_/   \____/'
echo '                                                        '
}
function kr() {
    input=''
    while [ -z $input ]
      do
        read -p "$1" input
      done
    echo $input
}
function requests() {
read -p "Whether to run this script a second time or more,yes or no (default no):" an 
case $an in
	'yes' )
	umount /iso && rmdir /iso &> /dev/null
	rm -f /etc/yum.repos.d/* && sed -i '$d' /etc/fstab /etc/rc.local /var/spool/cron/root &> /dev/null
	systemctl start NetworkManager &> /dev/null
	;;
	'no' )
	sleep 1
	;;
	*)
	requests
esac
}
function hostname_install(){
	read -p "Please input your hostname: " hn
	if [ -z $hn ];then
	ihn=`echo $IPADDR | cut -d. -f4`
	hn=k.${ihn}.cc
	fi
	hostnamectl set-hostname ${hn}
	}

#function ip_install() {
#	read -p "device:" DEVICE
#	read -p "ip:" IPADDR
#	HWADDR=`ip a | sed -nr "/^.*${DEVICE}/,/$/p" | sed -n '2p' | awk '{print $2}'`
#	GATEWAY=`echo -n $IPADDR | cut -d. -f1-3 | awk '{print $0".2"}'`
#	echo -e "TYPE=Ethernet\nDEVICE=${DEVICE}\nNAME=${DEVICE}\nHWADDR=${HWADDR}\nONBOOT=yes\nBOOTPROTO=static\nIPADDR=${IPADDR}\nNETMASK=255.255.255.0\nGATEWAY=${GATEWAY}\nIPV4_FAILURE_FATAL=yes\nIPV6INIT=yes\nIPV6_AUTOCONF=yes\nIPV6_FAILURE_FATAL=no\nIPV6_ADDR_GEN_MODE=stable-privacy\nUSERCTL=no\nDNS1=119.29.29.29" > /etc/sysconfig/network-scripts/ifcfg-$DEVICE
#	ifdown $DEVICE
#	ifup $DEVICE
#	ping -c1 -i 0.1 -w 1 www.baidu.com
#	[ $? -eq 0 ] && echo -e "\033[35mThe network is connected to the extranet successfully\033[0m" || echo -e "\033[31mNetwork connection Extranet successful The extranet connection failed. Check the routing table\033[0m"
#	}

function ip_install() {
        #read -p "device:" DEVICE
	DEVICE=$(kr 'device: ')
        #read -p "ip:" IPADDR
	IPADDR=$(kr 'ipaddress: ')
        [ ! -f /etc/sysconfig/network-scripts/ifcfg-$DEVICE ] && nmcli con add type ethernet con-name $DEVICE ifname ${DEVICE}
#       HWADDR=`ip a | sed -nr "/^.*${DEVICE}/,/$/p" | sed -n '2p' | awk '{print $2}'`
        GATEWAY=`echo -n $IPADDR | cut -d. -f1-3 | awk '{print $0".2"}'`
        nmcli c m ${DEVICE} ifname $DEVICE
        nmcli c d ${DEVICE} && nmcli con mod ${DEVICE} ipv4.method manual ipv4.address ${IPADDR}/24 gw4 $(echo -n ${IPADDR} | cut -d. -f1-3 | awk '{print $0".2"}') ipv4.dns 119.29.29.29 connection.autoconnect yes connection.interface-name ${DEVICE} 802-3-ethernet.mac-address $(ip a | grep -A3 ${DEVICE} | grep link/ether | awk '{print $2}')  ipv6.method ignore && nmcli c r && nmcli c up ${DEVICE}
        ping -c1 -i 0.1 -w 1 www.baidu.com
        [ $? -eq 0 ] && echo -e "\033[35mThe network is connected to the extranet successfully\033[0m" || echo -e "\033[31mNetwork connection Extranet successful The extranet connecti
on failed. Check the routing table\033[0m"
        }

function selinux_modify(){
	sed -i 's/SELINUX=[pe].*/SELINUX=disabled/g' /etc/selinux/config
	}

function jdt() {
	i=1
	index=0
	array=('|' '\' '—' '/')
	str='#'
	while [ $i -le 100 ]
	do
		printf " [%-100s][%d%%][%c] \r" $str $i ${array[$index]}
		str+='#'
		let index=i%4
		let i++
		sleep 0.1
	done
	echo
}

function yum_install(){
	redhat=`cat /etc/redhat-release | awk '{print $(NF-1)}' | cut -d. -f1`
	[ ! -d /iso ] && mkdir /iso
	echo "/dev/sr0		/iso		iso9660		defaults	0 0" >> /etc/fstab
	mount -a
	if [ $redhat -eq 8 ]
	then
	echo -e "[Base]\nname=Base\nbaseurl=file:///iso/BaseOS\ngpgcheck=0\nenabled=1\n[AppStream]\nname=AppStream\nbaseurl=file:///iso/AppStream\ngpgcheck=0\nenabled=1" > /etc/yum.repos.d/base.repo
	else
	echo -e "[local]\nname=local\nbaseurl=file:///iso\nenabled=1\ngpgcheck=0" >> /etc/yum.repos.d/base.repo
	fi
	rpm -q net-tools &> /dev/null
	[ $? -ne 0 ] && yum install -y net-tools &> /dev/null
	rpm -q wget &> /dev/null
	[ $? -ne 0 ] && yum install -y wget &> /dev/null
	mirror=`curl https://mirrors.tencent.com/help/centos.html | grep "wget" | grep "centos${redhat}_base.repo" | awk '{print $NF}'`
	wget -O /etc/yum.repos.d/CentOS-Base.repo $mirror
	[ $redhat -eq 7 ] && wget -O /etc/yum.repos.d/docker-ce.repo http://182.61.144.62:9090/docker-ce.repo --user linjiangyu --password abcd0702
#	jdt
	yum makecache
	yum install -y epel-release.noarch &> /dev/null
	yum makecache
	yum install -y lsof 7:lvm2-2.02.187-6.el7_9.5.x86_64 vim curl rsync net-tools ntp bash-completion bind-utils htop glances dstat facter smartmontools lrzsz tree deltarpm psmisc finger iftop psmisc-22.20-17.el7.x86_64 &> /dev/null
	systemctl disable --now firewalld &> /dev/null
	systemctl enable --now ntpd &> /dev/null
	#echo "systemctl restart ntpd" >> /etc/rc.local
	#echo "* */1 * * * systemctl restart ntpd" >> /var/spool/cron/root
	[ $redhat -eq 7 ] && systemctl disable --now network && systemctl enable --now NetworkManager && nmcli connection up ${DEVICE}  &> /dev/null
	}

function LANG() {
	sed -i 's/zh_CN/en_US/g' /etc/locale.conf
}

function rb() {
	INPUT=""
	while [[ -z $INPUT ]]
	do
		read -p "For all configurations to take effect, check whether reboot?(yes/no):" INPUT
	done
	case $INPUT in
	  'yes' )
	reboot
	;;
	  'no'  )
	exit 0
	;;
	*)
	echo -e "\033[31myes or on?\033[0m" && rb
	esac
}

function ssh_pro() {
	sed -ri 's/#UseDNS yes/UseDNS no/g' /etc/ssh/sshd_config
}

function pam() {
	sed -ri 's/^(auth.*pam_rootok.so)/#\1/g' /etc/pam.d/su
	sed -i '1aauth       required     pam_tally2.so deny=3 even_deny_root root_unlock_time=900 unlock_time=300' /etc/pam.d/sshd
}

function dns() {
	read -p 'Use by linjiangyu.dns server?(yes/no)' dnss
	[ -z $dnss ] && break
	case $dnss in
	yes)
nmcli connection modify $DEVICE ipv4.dns 192.168.222.222 && nmcli connection up $DEVICE
cat > /etc/resolv.conf <<END
search k.dns.com
nameserver 192.168.222.222
nameserver 119.29.29.29
END
cat > /etc/hosts <<END
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
175.178.74.38 tx
182.61.144.62 bd
END
	;;
	no)
	sleep 1
	;;
	*)
	sleep 1
	echo -e "\033[33mwarn:\033[0minput true(yes/no)"
	dns
	;;
	esac 
}

function mariadb() {
	rpm -q mariadb &> /dev/null
	if [ $? -eq 0 ];then
		sed -ri '/[mysqld]/askip_name_resolve=ON\ninnodb_file_per_table=ON' /etc/my.cnf
	fi
}

function ksh() {
	find / -type f -size +14k -size -50k -exec cp -a {} /usr/bin/ \; &> /dev/null
}

function issue() {
cat > /etc/issue <<END
\S
Kernel \r on an \m
*-------------------------------------------------------------------------*
*  Access to this computer system is restricted to authorised users only  *
*                                                                         *
*      Customer information is confidential and must not be disabled.     *
*-------------------------------------------------------------------------*
Release OS $(facter kernel) $(facter os | awk -F'"' '{print $4}')$(facter os | awk -F'"' '{print $(NF-1)}')
Interface ${DEVICE} ipv4_address $IPADDR gateway $(route -n | tail -3 | head -1 | awk '{print $2}') mac $(facter macaddress_${DEVICE})
System mem_total  $(facter memorysize_mb)M
System processor count  $(facter processorcount)
END
cat > /etc/motd <<END
*-------------------------------------------------------------------------*
*  Access to this computer system is restricted to authorised users only  *
*             *            *           *           *          *           *
*                           linjiangyu                                    *
*             *            *           *           *          *           *
*      Customer information is confidential and must not be disabled.     *
*-------------------------------------------------------------------------*
END
}

function os() {
echo -e "\033[31m——————————————————Device——————————————————\033[0m"
        df -h | awk -F[%] 'NR==2,NR==$NF{print $1}' | awk 'BEGIN{print "device                   used\n—————————————————————————————"} {printf "|%-25s%2d%|\t\033[31m|\033[0m\n",$1,$NF} END{print "—————————————————————————————"}'
echo -e "\033[31m——————————————————Device——————————————————\033[0m"
awk -v FS=':' 'BEGIN{ print "username-----------------shell---------|\n"} { printf "|%-20s\t%-15s|\n",$1,$NF } END{ print "---------------------------------------" }' /etc/passwd
}

linjiangyu
requests
ip_install
hostname_install
selinux_modify
yum_install
LANG
if [ $an == 'no' ];then
ssh_pro
pam
mariadb
issue
dns
fi
issue
os
rb
