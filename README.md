# Star2Star_DMZ

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
