# FP-Jarkom Kelompok A8



## 1. Topologi
![Screenshot 2024-12-18 170841](https://github.com/user-attachments/assets/94aee5b1-4c20-4391-9a77-f33a23563866)

## 2. Pembagian IP dan Rute Subnetting

**Metode VLSM**  
Prefix IP: **192.168.0.0/23**

### Tabel Pembagian IP

| **Nama Subnet** | **Rute**                                                                       | **Jumlah IP** | **Netmask** |
|-----------------|--------------------------------------------------------------------------------|--------------|------------|
| A1             | Lantai 1 > Switch 1 > Server dan Data Center > Dept IT > Dept HR               | 81           | /25        |
| A2             | Lantai 1 > Lantai 2                                                            | 2            | /30        |
| A3             | Lantai 2 > Switch 0 > Dept RnD > Dept Pemasaran > Dept Penjualan               | 91           | /25        |
| A4             | Lantai 2 > Lantai 3                                                            | 2            | /30        |
| A5             | Lantai 3 > Switch 2 > Dept Keuangan > Dept Legal                               | 41           | /26        |
| A6             | Lantai 3 > Lantai 4                                                            | 2            | /30        |
| A7             | Lantai 4 > Switch > Dept Manajemen > Dept CS                                   | 41           | /26        |
| A8             | Lantai 4 > Lantai 5                                                            | 2            | /30        |
| A9             | Lantai 5 > Switch > Dept Cysec > R Meeting > Depart HR                         | 51           | /26        |
| A10            | Cabang 2 > Server PT                                                          | 2            | /30        |
| A11            | Router Cabang > Router NAT                                                    | 2            | /30        |
| A12            | Lantai 5 > Router NAT                                                         | 2            | /30        |
| A13            | Router Cabang > Lantai 5 (GRE Tunnel)                                         | 2            | /30        |

**Total Jumlah IP:** 321  
**Prefix Netmask:** /23  

### Tabel IP Address Detail

| **Subnet** | **Network ID** | **Netmask**       | **Broadcast**    | **Range IP**                        |
|------------|----------------|-------------------|------------------|------------------------------------|
| A3         | 192.168.0.0    | 255.255.255.128   | 192.168.0.127    | 192.168.0.1 - 192.168.0.126         |
| A1         | 192.168.0.128  | 255.255.255.128   | 192.168.0.255    | 192.168.0.129 - 192.168.0.254       |
| A4         | 192.168.1.0    | 255.255.255.252   | 192.168.1.3      | 192.168.1.1 - 192.168.1.2           |
| A5         | 192.168.1.64   | 255.255.255.192   | 192.168.1.127    | 192.168.1.65 - 192.168.1.126        |
| A7         | 192.168.1.128  | 255.255.255.192   | 192.168.1.191    | 192.168.1.129 - 192.168.1.190       |
| A2         | 192.168.1.192  | 255.255.255.252   | 192.168.1.195    | 192.168.1.193 - 192.168.1.194       |
| A6         | 192.168.1.196  | 255.255.255.252   | 192.168.1.199    | 192.168.1.197 - 192.168.1.198       |
| A8         | 192.168.1.200  | 255.255.255.252   | 192.168.1.203    | 192.168.1.201 - 192.168.1.202       |
| A9         | 192.168.1.204  | 255.255.255.192   | 192.168.1.255    | 192.168.1.205 - 192.168.1.254       |
| A10        | 192.168.1.208  | 255.255.255.252   | 192.168.1.211    | 192.168.1.209 - 192.168.1.210       |
| A11        | 192.168.1.212  | 255.255.255.252   | 192.168.1.215    | 192.168.1.213 - 192.168.1.214       |
| A12        | 192.168.1.216  | 255.255.255.252   | 192.168.1.219    | 192.168.1.217 - 192.168.1.218       |
| A13        | 192.168.1.220  | 255.255.255.252   | 192.168.1.223    | 192.168.1.221 - 192.168.1.222       |

## 3. Konfigurasi Router dan Client

### A1
```
# Lantai 1 
enable
configure terminal
interface fa0/1
ip address 192.168.0.129 255.255.255.128
no shutdown

# Server dan Data Center
interface  fa0
IP Address: 192.168.0.130
Subnet Mask: 255.255.255.128
Gateway: 192.168.0.129

# Dept IT
interface  fa0
IP Address: 192.168.0.131
Subnet Mask: 255.255.255.128
Gateway: 192.168.0.129

# Dept HR
interface  fa0
IP Address: 192.168.0.132
Subnet Mask: 255.255.255.128
Gateway: 192.168.0.129
```
### A2
```
# Lantai 1
enable
configure terminal
interface fa0/0
ip address 192.168.1.193 255.255.255.252
no shutdown

# Lantai 2
enable
configure terminal
interface fa0/1
ip address 192.168.1.194 255.255.255.252
no shutdown
```
### A3
```
# Lantai 2
enable
configure terminal
interface fa1/0
ip address 192.168.0.1 255.255.255.128
no shutdown
ip dhcp excluded-address 192.168.0.1 192.168.0.4
ip dhcp pool Lantai2
network 192.168.0.0 255.255.255.128
default-router 192.168.0.1
exit
exit
write memory

# Dept Rnd
interface  fa0
IP Address: DHCP
Subnet Mask: DHCP
Gateway: DHCP

# Dept Pemasaran
interface  fa0
IP Address: DHCP
Subnet Mask: DHCP
Gateway: DHCP

# Dept Penjualan
interface  fa0
IP Address: DHCP
Subnet Mask: DHCP
Gateway: DHCP
```
### A4
```
# Lantai 2
enable
configure terminal
interface fa0/0
ip address 192.168.1.197 255.255.255.252
no shutdown

# Lantai 3
enable
configure terminal
interface fa0/1
ip address 192.168.1.198 255.255.255.252
no shutdown
```
### A5
```
# Lantai 3
enable
configure terminal
interface fa1/0
ip address 192.168.1.65 255.255.255.192
no shutdown

# Dept Keuangan
interface  fa0
IP Address: 192.168.1.66
Subnet Mask: 255.255.255.192
Gateway: 192.168.1.65

#Dept Legal
interface  fa0
IP Address: 192.168.1.67
Subnet Mask: 255.255.255.192
Gateway: 192.168.1.65
```
### A6
```
# Lantai 3
enable
configure terminal
interface fa0/0
ip address 192.168.1.201 255.255.255.252
no shutdown

# Lantai 4
enable
configure terminal
interface fa0/1
ip address 192.168.1.202 255.255.255.252
no shutdown
```
### A7
```
# Lantai 4
enable
configure terminal
interface fa1/0
ip address 192.168.1.129 255.255.255.192
no shutdown

# Dept Manajemen
interface  fa0
IP Address: 192.168.1.130
Subnet Mask: 255.255.255.192
Gateway: 192.168.1.129

# Dept Customer Service
interface  fa0
IP Address: 192.168.1.131
Subnet Mask: 255.255.255.192
Gateway: 192.168.1.129
```
### A8
```
# Lantai 4
enable
configure terminal
interface fa0/0
ip address 192.168.1.205 255.255.255.252
no shutdown

# Lantai 5
enable
configure terminal
interface fa0/1
ip address 192.168.1.206 255.255.255.252
no shutdown
```
### A9
```
# Lantai 5
enable
configure terminal
interface fa1/0
ip address 192.168.1.1 255.255.255.192
no shutdown

# Dept Cyber Security
interface  fa0
IP Address: 192.168.1.2
Subnet Mask: 255.255.255.192
Gateway: 192.168.1.1

# Ruang Meeting
interface  fa0
IP Address: 192.168.1.3
Subnet Mask: 255.255.255.192
Gateway: 192.168.1.1

# Depart HR
interface  fa0
IP Address: 192.168.1.4
Subnet Mask: 255.255.255.192
Gateway: 192.168.1.1
```
### A10
```
# Router Cabang
enable
configure terminal
interface fa0/1
ip address 192.168.1.209 255.255.255.252
no shutdown

# Cabang
interface  fa0
IP Address: 192.168.1.210
Subnet Mask: 255.255.255.252
Gateway: 192.168.1.209
```
### A11
```
# Router Cabang
enable
configure terminal
interface fa0/0
ip address 192.168.1.214 255.255.255.252
no shutdown

# Router NAT
enable
configure terminal
interface fa1/0
ip address 192.168.1.213 255.255.255.252
no shutdown
```
### A12
```
# Lantai 5
enable
configure terminal
interface fa0/0
ip address 192.168.1.218 255.255.255.252
no shutdown

# Router NAT
enable
configure terminal
interface fa0/0
ip address 192.168.1.217 255.255.255.252
no shutdown
```
### A13
```
# Lantai 5
interface Tunnel0
ip address 192.168.1.222 255.255.255.252
tunnel source FastEthernet0/0
tunnel destination 192.168.1.221
no shutdown

# Router Cabang
interface Tunnel0
ip address 192.168.1.221 255.255.255.252
tunnel source FastEthernet0/0
tunnel destination 192.168.1.222
no shutdown
```

## 4. Routing

### Lantai 1
```
enable
configure terminal
ip route 192.168.0.0 255.255.255.128 192.168.1.194
ip route 192.168.1.196 255.255.255.252 192.168.1.194
ip route 192.168.1.64 255.255.255.192 192.168.1.194
ip route 192.168.1.128 255.255.255.192 192.168.1.194
ip route 192.168.1.0 255.255.255.192 192.168.1.194
ip route 192.168.1.204 255.255.255.252 192.168.1.194
ip route 0.0.0.0 0.0.0.0 192.168.1.194
end
write memory
```
### Lantai 2
```
enable
configure terminal
ip route 192.168.0.128 255.255.255.128 192.168.1.193
ip route 192.168.1.200 255.255.255.252 192.168.1.198
ip route 192.168.1.64 255.255.255.192 192.168.1.198
ip route 192.168.1.128 255.255.255.192 192.168.1.198
ip route 192.168.1.0 255.255.255.192 192.168.1.198
ip route 192.168.1.204 255.255.255.252 192.168.1.198
ip route 0.0.0.0 0.0.0.0 192.168.1.198
end
write memory
```
### Lantai 3
```
enable
configure terminal
ip route 192.168.0.0 255.255.255.128 192.168.1.197
ip route 192.168.1.192 255.255.255.252 192.168.1.197
ip route 192.168.1.64 255.255.255.192 192.168.1.202
ip route 192.168.1.128 255.255.255.192 192.168.1.202
ip route 192.168.0.128 255.255.255.128 192.168.1.197
ip route 192.168.1.0 255.255.255.192 192.168.1.202
ip route 192.168.1.204 255.255.255.252 192.168.1.202
ip route 0.0.0.0 0.0.0.0 192.168.1.202
end
write memory
```
### Lantai 4
```
enable
configure terminal
ip route 192.168.1.64 255.255.255.192 192.168.1.201
ip route 192.168.1.0 255.255.255.192 192.168.1.206
ip route 192.168.0.128 255.255.255.128 192.168.1.201
ip route 192.168.0.0 255.255.255.128 192.168.1.201
ip route 192.168.1.196 255.255.255.252 192.168.1.201
ip route 192.168.1.192 255.255.255.252 192.168.1.201
ip route 0.0.0.0 0.0.0.0 192.168.1.206
end
write memory
```
### Lantai 5
```
enable
configure terminal
ip route 192.168.1.128 255.255.255.192 192.168.1.205
ip route 192.168.1.200 255.255.255.252 192.168.1.205
ip route 192.168.1.64 255.255.255.192 192.168.1.205
ip route 192.168.0.0 255.255.255.128 192.168.1.205
ip route 192.168.0.128 255.255.255.128 192.168.1.205
ip route 192.168.1.196 255.255.255.252 192.168.1.205
ip route 192.168.1.192 255.255.255.252 192.168.1.205
ip route 0.0.0.0 0.0.0.0 192.168.1.217
end
write memory
```
### Router Cabang
```
enable
configure terminal
ip route 0.0.0.0 0.0.0.0 192.168.1.213
ip route 192.168.1.216 255.255.255.252 192.168.1.213
end
write memory
```

## 5. NAT

### Router NAT
```
enable
configure terminal

interface FastEthernet1/0
 ip address 192.168.1.213 255.255.255.252
 ip nat inside
 duplex auto
 speed auto

interface FastEthernet0/1
 ip address 192.168.1.217 255.255.255.252
 ip nat inside
 duplex auto
 speed auto

interface FastEthernet0/0
 ip address dhcp
 ip nat outside
 duplex auto
 speed auto

interface FastEthernet1/1
 no ip address
 duplex auto
 speed auto
 shutdown

interface Vlan1
 no ip address
 shutdown

ip nat inside source list 1 interface FastEthernet0/0 overload
ip classless
access-list 1 permit any
ip route 0.0.0.0 0.0.0.0 dhcp

end
write memory
```
### Lantai 5
```
enable
configure terminal

interface FastEthernet0/1
 ip address 192.168.1.206 255.255.255.252
 ip nat inside
 duplex auto
 speed auto

interface FastEthernet1/0
 ip address 192.168.1.1 255.255.255.192
 ip nat inside
 duplex auto
 speed auto

interface FastEthernet0/0
 ip address 192.168.1.218 255.255.255.252
 ip nat outside
 duplex auto
 speed auto

interface FastEthernet1/1
 no ip address
 shutdown

interface Vlan1
 no ip address
 shutdown

ip nat inside source list 1 interface FastEthernet0/0 overload
access-list 1 permit any

end
write memory
```
### Testing

## 6. GRE Tunnel

### A13
```
# Lantai 5
interface Tunnel0
ip address 192.168.1.222 255.255.255.252
tunnel source FastEthernet0/0
tunnel destination 192.168.1.221
no shutdown

# Router Cabang
interface Tunnel0
ip address 192.168.1.221 255.255.255.252
tunnel source FastEthernet0/0
tunnel destination 192.168.1.222
no shutdown
```
### Test Ping
