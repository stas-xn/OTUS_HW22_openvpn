### Домашнее задание
VPN
1. Между двумя виртуалками поднять vpn в режимах
- tun
- tap
Прочуствовать разницу.

2. Поднять RAS на базе OpenVPN с клиентскими сертификатами, подключиться с локальной машины на виртуалку

3*. Самостоятельно изучить, поднять ocserv и подключиться с хоста к виртуалке 
### 1. Между двумя виртуалками поднять vpn  
- Запустить стенд  ```vagrant up && ansible-playbook
 start yaml ``` 
 - Стэнд поднимится с  openvpn udp
 - Измерит скорость соеденения ```ansible-playbook iperf.yaml -vv```
 - Изменить протокол на tcp ``` ansible-playbook chenge_proto_to_tcp.yml```
 - Снова измерит скорость соеденения ```ansible-playbook iperf.yaml -vv```

### Вывод iperf
#### OpenVPN with proto tcp

```
ok: [openvpn-client] => {
    "result.stdout_lines": [
        "------------------------------------------------------------", 
        "Client connecting to 172.16.10.1, TCP port 5001", 
        "TCP window size: 45.0 KByte (default)", 
        "------------------------------------------------------------", 
        "[  3] local 172.16.10.6 port 60468 connected with 172.16.10.1 port 5001", 
        "[ ID] Interval       Transfer     Bandwidth", 
        "[  3]  0.0-10.0 sec   413 MBytes   345 Mbits/sec"
    ]
}
```
#### OpenVPN with proto udp

```
ok: [openvpn-client] => {
    "result.stdout_lines": [
        "------------------------------------------------------------", 
        "Client connecting to 172.16.10.1, TCP port 5001", 
        "TCP window size: 81.0 KByte (default)", 
        "------------------------------------------------------------", 
        "[  3] local 172.16.10.6 port 60474 connected with 172.16.10.1 port 5001", 
        "[ ID] Interval       Transfer     Bandwidth", 
        "[  3]  0.0-10.0 sec  92.0 MBytes  77.1 Mbits/sec"
    ]
}
```
