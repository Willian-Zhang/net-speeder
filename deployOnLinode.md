mkdir net-speeder
cd net-speeder

wget http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm

rpm -ivh epel-release-6-8.noarch.rpm

wget https://raw.githubusercontent.com/snooda/net-speeder/master/build.sh
wget https://raw.githubusercontent.com/snooda/net-speeder/master/net_speeder.c


nano speeeeed.sh
``` sh
if [ -f /proc/user_beancounters ] || [ -d /proc/bc ]; then
    sh build.sh -DCOOKED
    INTERFACE=venet0
else
    sh build.sh
    INTERFACE=eth0
fi

NS_PATH=/usr/local/net_speeder
mkdir -p $NS_PATH
cp -Rf net_speeder $NS_PATH

echo -e "\033[36m net_speeder installed. \033[0m"
echo -e "\033[36m Usage: nohup ${NS_PATH}/net_speeder $INTERFACE \"ip\" >/dev/null 2>&1 & \033[0m"
```
sh speeeeed.sh
