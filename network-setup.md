ISR4331 Router1

ip address 168.90.0.1
2960-24TT Switch1
PC-PT PC1
PC-PT PC2
PC-PT PC4
Laptop-PT Laptop1
Server-PT Server1

ip adress 210.3.14.1
2960-24TT Switch2
Server-PT Fa0 Server2
Server-PT Server3
PC-PT PC3
PC-PT PC5

# DHCP Configuration Steps (Switch1)
enable
config t
interface GigabitEthernet 0/0/0
ip address 168.90.0.1 255.255.255.0 
no shutdown 
exit
ip dhcp pool FIRST-POOL
network 168.90.0.0 255.255.255.0
default-router 168.90.0.1
dns-server 168.90.0.254
exit

# DHCP Configuration Steps (Switch2)
enable
config t
interface GigabitEthernet 0/0/1
ip address 210.3.14.1 255.255.255.0 
no shutdown 
exit
ip dhcp pool FIRST-POOL
network 210.3.14.0 255.255.255.0
default-router 210.3.14.1
dns-server 210.3.14.254
exit

# DHCP Configuration Steps

Click on the router, then CLI field. Message below appeared.
'Press RETURN to get started!'
I just click 'enter' on my keyboard.
After that, I insert command 'enable' after 'config t' to enter configuration commands.
For this assignmet task, I separated Switch1 (left side, connection Gig 0/0/0 Fa 0/1) and Switch2 (right, side connection Gig 0/0/1 Fa 0/1) for better organization. 
'interface GigabitEthernet 0/0/0' this is for the Switch1, Switch2 required a little bit changes 'interface GigabitEthernet 0/0/1'.
'ip address 168.90.0.1 255.255.255.0' this command added ip address and also subnet mask which is same for the Switch1 and Switch2, 
Switch2 required another ip adress like in assignmet description 'ip adress 210.3.14.1 255.255.255.0'
'no shutdown' this command enable router to be on all the timme
'exit' I am done with this setup, and write exit so I can contiune setuping DHCP.

'ip dhcp pool FIRST-POOL' this is starting command for DHCP setup, 'FIRST-POOL' is just a name for specific Switch, in this case, it is for Switch1,
for the Switch2 name is 'SECOND-POOL' it is good practice to add a unique name, for me, if I didn't add a unique name, 
I will not be able to call this specific part of the code because I needed to apply some changes.
'network 168.90.0.0 255.255.255.0' this is network addres for Switch1 also subnet mask which is same for both Switches, for Switch2 it is network 210.3.14.0 255.255.255.0
'default-router 168.90.0.1' this line specify the default gateway, for Switch2 is default-router 210.3.14.1.
'dns-server 168.90.0.254' for the Switch2 is 'dns-server 210.3.14.254' this is not written in assignmet, but I added DNS
'exit' this is the last command line, I am done with configuration.

# Conclusion
DHCP Configuration is not that hard, all you need it good connection between devices, and after first setup for one Switch for the other Switch commands are the same,
you just need to be careful with changes which I mention line by line.