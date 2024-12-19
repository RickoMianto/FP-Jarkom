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

```
### A3
```

```
### A4
```

```
### A5
```

```
### A6
```

```
### A7
```

```
### A8
```

```
### A9
```

```
### A10
```

```
### A11
```

```
### A12
```

```

## 4. Routing



## 5. NAT



## 6. GRE Tunnel
