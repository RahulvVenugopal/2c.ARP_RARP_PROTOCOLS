# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
```
import random
import time
class ARP:
    def __init__(self):
        self.cache = {}

    def resolve(self, ip):
        if ip in self.cache:
            print("IP {} resolved to MAC {} from cache.".format(ip, self.cache[ip]))
            return self.cache[ip]
        else:
            print("ARP Request: Who has IP {}?".format(ip))
            mac = self.generate_mac()
            self.cache[ip] = mac
            print("ARP Response: IP {} is at MAC {}".format(ip, mac))
            return mac

    def generate_mac(self):
        mac = [random.choice('0123456789ABCDEF') for _ in range(12)]
        return ':'.join(''.join(mac[i:i+2]) for i in range(0, 12, 2))
if __name__ == "__main__":
    arp = ARP()
    print("\nSimulating ARP:")
    print(arp.resolve("192.168.0.1"))
    print(arp.resolve("192.168.0.2"))
    print(arp.resolve("192.168.0.1"))
```
## OUPUT - ARP
![Screenshot (138)1](https://github.com/RahulvVenugopal/2c.ARP_RARP_PROTOCOLS/assets/144132514/0074680d-67bd-41df-bbb8-10cf318c68f8)

## PROGRAM - RARP
```
class RARP:
    def __init__(self):
        self.cache = {}

    def resolve(self, mac):
        if mac in self.cache:
            print("MAC {} resolved to IP {} from cache.".format(mac, self.cache[mac]))
            return self.cache[mac]
        else:
            print("RARP Request: Who has MAC {}?".format(mac))
            ip = self.generate_ip()
            self.cache[mac] = ip
            print("RARP Response: MAC {} is at IP {}".format(mac, ip))
            return ip

    def generate_ip(self):
        return '.'.join(str(random.randint(0, 255)) for _ in range(4))
if __name__ == "__main__":
    rarp = RARP()
    print("\nSimulating RARP:")
    print(rarp.resolve("AA:BB:CC:DD:EE:FF"))
    print(rarp.resolve("AA:BB:CC:DD:EE:FF"))
    print(rarp.resolve("11:22:33:44:55:66"))
```
## OUPUT -RARP
![Screenshot (138)](https://github.com/RahulvVenugopal/2c.ARP_RARP_PROTOCOLS/assets/144132514/3eb28644-bb4d-40f1-ad57-e62cc7486dd8)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
