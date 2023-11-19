# Jarkom-Modul-3-A18-2023

- [Jarkom-Modul-3-A18-2023](#jarkom-modul-3-a18-2023)
  - [Anggota](#anggota)
  - [Konfigurasi Node](#konfigurasi-node)
  - [Soal](#soal)
    - [0](#0)
    - [1](#1)
    - [2 - 5](#2---5)
    - [6](#6)
    - [7](#7)
    - [13](#13)
    - [14](#14)
    - [15 - 17](#15---17)

## Anggota

|     | Nama                      | NRP        |
| --- | ------------------------- | ---------- |
| 1   | SATRIA SULTHAN SABILILLAH | 5025201267 |
| 2   | Urdhanaka Aptanagi        | 5025211123 |

## Konfigurasi Node

- Aura (Router)

  ```shell
  auto eth0
  iface eth0 inet dhcp

  auto eth1
  iface eth1 inet static
  address 10.8.1.0
  netmask 255.255.255.0

  auto eth2
  iface eth2 inet static
  address 10.8.2.0
  netmask 255.255.255.0

  auto eth3
  iface eth3 inet static
  address 10.8.3.0
  netmask 255.255.255.0

  auto eth4
  iface eth4 inet static
  address 10.8.4.0
  netmask 255.255.255.0
  ```

- Himmel (DHCP Server)

  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.1.1
  netmask 255.255.255.0
  gateway 10.8.1.0
  ```

- Heiter (DNS Server)

  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.1.2
  netmask 255.255.255.0
  gateway 10.8.1.0
  ```

- Denken (Database Server)

  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.2.1
  netmask 255.255.255.0
  gateway 10.8.2.0
  ```

- Eisen (Load Balancer)

  ```shell
  auto eth0
  iface eth0 inet static
  address 10.8.2.2
  netmask 255.255.255.0
  gateway 10.8.2.0
  ```

## Soal

### 0

- /etc/bind/named.conf.local

![image](https://user-images.githubusercontent.com/46347836/284059100-c4ebd638-1f3b-47c7-aaf2-2fe9b6c6cb37.png)

- /etc/bind/named.conf.options

![image](https://user-images.githubusercontent.com/46347836/284059409-e34d20a7-710d-4758-914e-e02737c84346.png)

- /etc/bind/domain/riegel.canyon.a18.com

![image](https://user-images.githubusercontent.com/46347836/284059479-e46abac6-79db-425d-bd71-b01961313aed.png)

- /etc/bind/domain/granz.channel.a18.com

![image](https://user-images.githubusercontent.com/46347836/284059517-4faced52-858d-49b6-8b2d-0dc6ca3a7912.png)

- script DNS Server

![image](https://user-images.githubusercontent.com/46347836/284059645-4076be2e-8a49-4327-afe2-eada795cd8f0.png)

### 1

![topologi](https://user-images.githubusercontent.com/46347836/283056647-83ccd085-9555-4261-b007-7649a2ba7a65.png)

### 2 - 5

- DHCP Server (Himmel)

  - dhcpd.conf

  ![image](https://user-images.githubusercontent.com/46347836/284059874-849268f8-382a-4f7f-ad2d-5d7fe4970de2.png)

  - isc-dhcp-server
  
  ![image](https://user-images.githubusercontent.com/46347836/284060016-0f9ac385-e8e0-419c-ae55-ff5ed5865816.png)

  - script DHCP Server

  ![image](https://user-images.githubusercontent.com/46347836/284060227-cb2835d8-d18d-4aac-9c19-3e2f22db954f.png)

- DHCP Relay (Aura)

  - isc-dhcp-relay
  
  ![image](https://user-images.githubusercontent.com/46347836/284060642-10189d13-004d-4214-9e02-87544dda6841.png)

  - sysctl.conf

  ![image](https://user-images.githubusercontent.com/46347836/284060725-0e8d0bd2-1757-49ce-9c15-1f50f047d180.png)

  - script DHCP Relay

  ![image](https://user-images.githubusercontent.com/46347836/284060904-4d2d7500-e649-4a95-b554-f1b62c8dd255.png)

### 6

Untuk soal 6, karena konfigurasi untuk ketiga worker kurang lebih sama, maka konfigurasi yang ditampilkan hanya konfigurasi pada worker Lawine saja

- granz-sites
  
![image](https://user-images.githubusercontent.com/46347836/284061154-83d32101-2d23-45fb-b97b-905dcf9d30c3.png)

- script worker

![image](https://user-images.githubusercontent.com/46347836/284061213-b28e0be6-1cfe-4646-a4b9-62d2510ac17b.png)

### 7

Untuk soal nomor 7, konfigurasi resource server ini dilakukan di load balancer, yaitu Eisen

- script Load Balancer

![image](https://user-images.githubusercontent.com/46347836/284062965-03bee344-cf8d-4370-9da1-82578da17c23.png)

(Konfigurasi di atas sudah mencakup konfigurasi untuk soal nomor 10, 11 dan 12)

Untuk weight, kami buat perbandingannya adalah 8:4:1

### 13

- Database server (Denken)

  - my.cnf

  ![image](https://user-images.githubusercontent.com/46347836/284063238-e151093b-b102-4f91-96af-09606492ae33.png)

  - script Database server
  
  ![image](https://user-images.githubusercontent.com/46347836/284063274-57cb6126-4acb-4976-bb29-611ad7c45925.png)

### 14

Untuk soal 14, karena konfigurasi untuk ketiga worker kurang lebih sama, maka konfigurasi yang ditampilkan hanya konfigurasi pada worker Frieren saja

- riegel-sites

![image](https://user-images.githubusercontent.com/46347836/284063491-556a71f9-b768-4707-874a-392a00a5b7e5.png)

- script worker

![image](https://user-images.githubusercontent.com/46347836/284063552-02bbd7f7-1b00-4cca-8966-0bdb378e2acc.png)

![image](https://user-images.githubusercontent.com/46347836/284063586-934c7493-5696-4433-a268-2aafb8829341.png)

### 15 - 17

![image](https://user-images.githubusercontent.com/46347836/284063758-30570b37-d7cc-40bb-bfff-44b49260957d.png)
