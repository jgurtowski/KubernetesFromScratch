
# IPV6

IPV6 has been the future for a long time, yet its usage is not as wide spread
as one would imagine. Iphones and other consumer devices will use IPv6, but a lot of IT infrastructure still relies on IPV4.

A few interesting things about IPv6: 1.) It allows for multipel address to be attached to a single physical interface. 2.) A security feature, the outgoing connection ip gets rotated occassionally to reduce tracking. 3.) A router is not need to assign an IP, the host can randomly generate its IP. However, the router typically provides a subdomain in which the host can generate its IP. 

Local Addressing Explained: [https://blog.apnic.net/2020/05/20/getting-ipv6-private-addressing-right/](https://blog.apnic.net/2020/05/20/getting-ipv6-private-addressing-right/)

For the Kube Cluster, setting a static ipv6 IP is probably not the canonical way of implementing a v6 network. It is probably better to allow the router to provide a subnet and allow autoconfig. However, since we're going to be putting the address in a lot of config files, lets just set a static ip.

We can generate a 40bit prefix for the ipv6 address randomly. But this is not preferred, there should be a seed using your mac address. 

To see hex :
```
dd if=/dev/urandom bs=1 count=5 | hexdump -x 
```

Linux automatically generates a IPV6 address for you, to disable that
```
echo "net.ipv6.conf.eno3.autoconf=0" > /etc/sysctl.d/40-ipv6.conf  
reboot
```

We don't want dhcpcd to configure anything either
```
edit /etc/dhcpcd.conf

remove:
persistent
slaac private
option classless_static_routes

add:
nodhcp6
ipv6ra_noautoconf
interface eno3
static ip6_address=XXXX:xxxx:xxx:xx
```

# Conclusion

IPv6 works by default on most systems. Your distro will likely assign a v6 ip
to the NIC. However, from a sys admin prespective, the transition from ipv4 to ipv6 will require some additional knowledge.