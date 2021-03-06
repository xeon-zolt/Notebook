All raspberry devices MAC addresses started with <b>B8:27:EB.</b>

So, on *nix systems, this can be accomplished by executing the following command:

```sudo nmap -sP 192.168.1.0/24 | awk '/^Nmap/{ip=$NF}/B8:27:EB/{print ip}'```

where 192.168.1.* will be your local network mask. You will get an answer like:

```Nmap scan report for raspberrypi.localnetwork.lan (192.168.1.179)```

The 192.168.1.179 is the Raspberry Pi IP address on you network.

# or
may not always work depends on hosts which have made it into your arp tables

```arp -na | grep -i b8:27:eb ```

# Finally
final command after combining above

```sudo nmap -sP $(nmcli | grep -Po '(?<=inet4\s)[^\s]*') | awk '/^Nmap/{ip=$NF}/B8:27:EB/{print ip}'```

and can be used for ssh like or maybe you can add sshpass or create a script with password using expect or use sshkey 
 
```ssh alarm@$(sudo nmap -sP $(nmcli | grep -Po '(?<=inet4\s)[^\s]*') | awk '/^Nmap/{ip=$NF}/B8:27:EB/{print ip}')```
