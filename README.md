# Star2Star_DMZ

Set Star2Star MidDbrain DMZ firewall rules

---
On host machine save the following rules below to a `notepad` text document called `s2sdmz.txt`

---
SCP DMZ rules onto the MidBrain
```bash
scp C:\\PATH\TO\s2sdmz.txt root@192.168.1.1:/root
```

*Select the document in file explorer and click `Copy Path` to get the absolute path*
> ![Copy Document Path](/assets/copy_path.png)

*SCP example*
> ![Star2Star DMZ SCP Command Example](/assets/s2s_dmz_scp.png)

---
SSH into the MidBrain and run the following commands:
```bash
# Cat the DMZ rules into /etc/config/firewall.
# Make sure the there are double `>>`. 
# A single `>` will overwrite the firewall configuration file.
cat /root/s2sdmz.txt >> /etc/config/firewall

# Reload the MidBrain firewall
/etc/init.d/firewall reload
```

The MidBrain now has the required DMZ rules for Star2Star phones

---
## s2sdmz.txt
```txt

config redirect
	option target 'DNAT'
	option src 'WAN'
	option dest 'LAN'
	option proto 'tcp udp'
	option name 'DMZ'
	option src_dport '2160'
	option dest_ip '192.168.1.5'

config redirect
	option target 'DNAT'
	list proto 'udp'
	option src 'WAN'
	option src_dport '10000-40000'
	option dest 'LAN'
	option dest_ip '192.168.1.5'
	option name 'DMZ-RTP'

config redirect
	option target 'DNAT'
	option name 'DMZ-NTP'
	list proto 'tcp'
	option src 'WAN'
	option src_dport '123'
	option dest 'LAN'
	option dest_ip '192.168.1.5'

config redirect
	option target 'DNAT'
	option name 'DMZ-22'
	option src 'WAN'
	option src_dport '22'
	option dest 'LAN'
	option dest_ip '192.168.1.5'

config redirect
	option target 'DNAT'
	option src 'WAN'
	option src_dport '222'
	option dest 'LAN'
	option dest_ip '192.168.1.5'
	option name 'DMZ-2222'

config redirect
	option target 'DNAT'
	option name 'DMZ-5060'
	option src 'WAN'
	option src_dport '5060'
	option dest 'LAN'
	option dest_ip '192.168.1.5'
	list proto 'tcp'
	list proto 'udp'

config redirect
	option target 'DNAT'
	option name 'DMZ-10000-20000'
	option src 'WAN'
	option src_dport '10000-20000'
	option dest 'LAN'
	option dest_ip '192.168.1.5'
	list proto 'tcp'
	list proto 'udp'

config redirect
	option target 'DNAT'
	option name 'DMZ-8021'
	option src 'WAN'
	option src_dport '8021'
	option dest 'LAN'
	option dest_ip '192.168.1.5'
	list proto 'tcp'
	list proto 'udp'

config redirect
	option target 'DNAT'
	option name 'DMZ-443'
	option src 'WAN'
	option src_dport '443'
	option dest 'LAN'
	option dest_ip '192.168.1.5'

```
