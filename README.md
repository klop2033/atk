# Домашнее задание «Уязвимости и атаки на информационные системы» - Фролов КС

### Задание 1

Скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/.

Это типовая ОС для экспериментов в области информационной безопасности, с которой следует начать при анализе уязвимостей.

Просканируйте эту виртуальную машину, используя **nmap**.

Попробуйте найти уязвимости, которым подвержена эта виртуальная машина.

Сами уязвимости можно поискать на сайте https://www.exploit-db.com/.

Для этого нужно в поиске ввести название сетевой службы, обнаруженной на атакуемой машине, и выбрать подходящие по версии уязвимости.

Ответьте на следующие вопросы:

- Какие сетевые службы в ней разрешены?
- Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)
  
*Приведите ответ в свободной форме.*  

### Ответ: 
```bash
Starting Nmap 7.80 ( https://nmap.org ) at 2025-04-13 19:37 MSK
Nmap scan report for 192.168.0.128
Host is up (0.0057s latency).
Not shown: 977 closed ports
PORT     STATE SERVICE     VERSION
21/tcp   open  ftp         vsftpd 2.3.4
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to 192.168.0.125
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      vsFTPd 2.3.4 - secure, fast, stable
|_End of status
22/tcp   open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
| ssh-hostkey: 
|   1024 60:0f:cf:e1:c0:5f:6a:74:d6:90:24:fa:c4:d5:6c:cd (DSA)
|_  2048 56:56:24:0f:21:1d:de:a7:2b:ae:61:b1:24:3d:e8:f3 (RSA)
23/tcp   open  telnet      Linux telnetd
25/tcp   open  smtp        Postfix smtpd
|_smtp-commands: metasploitable.localdomain, PIPELINING, SIZE 10240000, VRFY, ETRN, STARTTLS, ENHANCEDSTATUSCODES, 8BITMIME, DSN, 
|_ssl-date: 2025-04-13T16:36:36+00:00; -56s from scanner time.
| sslv2: 
|   SSLv2 supported
|   ciphers: 
|     SSL2_DES_64_CBC_WITH_MD5
|     SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
|     SSL2_RC4_128_WITH_MD5
|     SSL2_DES_192_EDE3_CBC_WITH_MD5
|     SSL2_RC2_128_CBC_WITH_MD5
|_    SSL2_RC4_128_EXPORT40_WITH_MD5
53/tcp   open  domain      ISC BIND 9.4.2
| dns-nsid: 
|_  bind.version: 9.4.2
80/tcp   open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
|_http-server-header: Apache/2.2.8 (Ubuntu) DAV/2
|_http-title: Metasploitable2 - Linux
111/tcp  open  rpcbind     2 (RPC #100000)
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
512/tcp  open  exec        netkit-rsh rexecd
513/tcp  open  login?
514/tcp  open  tcpwrapped
1099/tcp open  java-rmi    GNU Classpath grmiregistry
1524/tcp open  bindshell   Metasploitable root shell
2049/tcp open  nfs         2-4 (RPC #100003)
2121/tcp open  ftp         ProFTPD 1.3.1
3306/tcp open  mysql       MySQL 5.0.51a-3ubuntu5
| mysql-info: 
|   Protocol: 10
|   Version: 5.0.51a-3ubuntu5
|   Thread ID: 12
|   Capabilities flags: 43564
|   Some Capabilities: SupportsTransactions, Support41Auth, SupportsCompression, Speaks41ProtocolNew, SwitchToSSLAfterHandshake, ConnectWithDatabase, LongColumnFlag
|   Status: Autocommit
|_  Salt: tagd>I6oP!R\Usg(1^d[
5432/tcp open  postgresql  PostgreSQL DB 8.3.0 - 8.3.7
|_ssl-date: 2025-04-13T16:36:36+00:00; -56s from scanner time.
5900/tcp open  vnc         VNC (protocol 3.3)
| vnc-info: 
|   Protocol version: 3.3
|   Security types: 
|_    VNC Authentication (2)
6000/tcp open  X11         (access denied)
6667/tcp open  irc         UnrealIRCd
| irc-info: 
|   users: 1
|   servers: 1
|   lusers: 1
|   lservers: 0
|   server: irc.Metasploitable.LAN
|   version: Unreal3.2.8.1. irc.Metasploitable.LAN 
|   uptime: 0 days, 1:02:02
|   source ident: nmap
|   source host: 9F1E162B.F0D9233E.FFFA6D49.IP
|_  error: Closing Link: qpjynqymc[192.168.0.125] (Quit: qpjynqymc)
8009/tcp open  ajp13       Apache Jserv (Protocol v1.3)
|_ajp-methods: Failed to get a valid response for the OPTION request
8180/tcp open  http        Apache Tomcat/Coyote JSP engine 1.1
|_http-favicon: Apache Tomcat
|_http-server-header: Apache-Coyote/1.1
|_http-title: Apache Tomcat/5.5
Service Info: Hosts:  metasploitable.localdomain, irc.Metasploitable.LAN; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_clock-skew: mean: -56s, deviation: 0s, median: -56s
|_ms-sql-info: ERROR: Script execution failed (use -d to debug)
|_nbstat: NetBIOS name: METASPLOITABLE, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
|_smb-os-discovery: ERROR: Script execution failed (use -d to debug)
|_smb-security-mode: ERROR: Script execution failed (use -d to debug)
|_smb2-time: Protocol negotiation failed (SMB2)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 36.67 seconds
```
### Обнаруженные сервисы:

21/tcp - ftp
22/tcp - OpenSSH
23/tcp - telnet
25/tcp - smtp
53/tcp - dns 
80/tcp - Apache
139/tcp- Samba (smb)
3306/tcp - mysql
5432/tcp - PostgreSQL
8180/tcp - Apache Tomcat

### Уязвимости: 

1 - MySQL 5.0.x - Single Row SubSelect Remote Denial of Service ( https://www.exploit-db.com/exploits/29724 ) - Злоумышленник может воспользоваться этой проблемой, чтобы вызвать сбой приложения, лишив доступа пользователей.

2 - Apache < 2.2.34 / < 2.4.27 - OPTIONS Memory Leak ( https://www.exploit-db.com/exploits/42745 ) - позволяет злоумышленникам читать конфиденциальные данные из памяти процесса

3 - Samba 3.4.5 - Symlink Directory Traversal ( https://www.exploit-db.com/exploits/33599 ) - позволяют злоумышленнику получить доступ к файлам за пределами корневого каталога пользователя Samba, чтобы получить конфиденциальную информацию и выполнить другие атаки.

### Задание 2

Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.

Запишите сеансы сканирования в Wireshark.

Ответьте на следующие вопросы:

- Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?
- Как отвечает сервер?

*Приведите ответ в свободной форме.*

---

## Ответ: 

### *SYN*

```bash
Nmap scan report for 192.168.0.128
Host is up (0.0030s latency).
Not shown: 988 closed ports
PORT    STATE SERVICE
21/tcp  open  ftp
22/tcp  open  ssh
23/tcp  open  telnet
25/tcp  open  smtp
53/tcp  open  domain
80/tcp  open  http
111/tcp open  rpcbind
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
512/tcp open  exec
513/tcp open  login
514/tcp open  shell

```

```

При SYN запросе отправляется пакет с флагом SYN в ответ приходит SYN-ASK (порт открыт) либо RST (закрыт)

```


### *FIN*

```bash

# Nmap 7.80 scan initiated Sun Apr 13 22:16:42 2025 as: nmap -sF -p 1-1000 -oN /home/kirtest/net/atk/fin.txt 192.168.0.128

Nmap scan report for 192.168.0.128
Host is up (0.0020s latency).
Not shown: 988 closed ports
PORT    STATE         SERVICE
21/tcp  open|filtered ftp
22/tcp  open|filtered ssh
23/tcp  open|filtered telnet
25/tcp  open|filtered smtp
53/tcp  open|filtered domain
80/tcp  open|filtered http
111/tcp open|filtered rpcbind
139/tcp open|filtered netbios-ssn
445/tcp open|filtered microsoft-ds
512/tcp open|filtered exec
513/tcp open|filtered login
514/tcp open|filtered shell
MAC Address: 08:00:27:34:E2:AB (Oracle VirtualBox virtual NIC)

# Nmap done at Sun Apr 13 22:16:43 2025 -- 1 IP address (1 host up) scanned in 1.75 seconds

```

```
Отправляется пакет с флагом FIN нет ответа (порт открыт, либо отсеян фаерволом 'filtered' ), RST (закрыт)

```

### *XMAS*

```bash
# Nmap 7.80 scan initiated Sun Apr 13 22:15:51 2025 as: nmap -sX -p 1-1000 -oN /home/kirtest/net/atk/xmas.txt 192.168.0.128
Nmap scan report for 192.168.0.128
Host is up (0.0026s latency).
Not shown: 988 closed ports
PORT    STATE         SERVICE
21/tcp  open|filtered ftp
22/tcp  open|filtered ssh
23/tcp  open|filtered telnet
25/tcp  open|filtered smtp
53/tcp  open|filtered domain
80/tcp  open|filtered http
111/tcp open|filtered rpcbind
139/tcp open|filtered netbios-ssn
445/tcp open|filtered microsoft-ds
512/tcp open|filtered exec
513/tcp open|filtered login
514/tcp open|filtered shell
MAC Address: 08:00:27:34:E2:AB (Oracle VirtualBox virtual NIC)

# Nmap done at Sun Apr 13 22:15:52 2025 -- 1 IP address (1 host up) scanned in 1.74 seconds
```

```
Отправляется пакет с флагом FIN,PSH,URG нет ответа  (порт открыт, либо отсеян фаерволом 'filtered'), RST (закрыт)
```
### *UDP*

```bash

# Nmap 7.80 scan initiated Sun Apr 13 22:22:37 2025 as: nmap -sU -p 1-500 -oN /home/kirtest/net/atk/udp.txt 192.168.0.128
Nmap scan report for 192.168.0.128
Host is up (0.0040s latency).
Not shown: 494 closed ports
PORT    STATE         SERVICE
53/udp  open          domain
68/udp  open|filtered dhcpc
69/udp  open|filtered tftp
111/udp open          rpcbind
137/udp open          netbios-ns
138/udp open|filtered netbios-dgm
MAC Address: 08:00:27:34:E2:AB (Oracle VirtualBox virtual NIC)

# Nmap done at Sun Apr 13 22:31:33 2025 -- 1 IP address (1 host up) scanned in 536.29 seconds

```

```
Отправляет UDP пакеты, в ответ получает UDP пакет (порт открыт), ICMP (порт закрыт) 

```
