# otus_linux_hw17
Описание/Пошаговая инструкция выполнения домашнего задания:
Необходимо:

снять дамп сессии работы с сайтом по протоколу HTTP с помощью tcpdump и фильтров
сохранить дамп в файл
описать процесс установления соединения на основе дампа


```
Флаги соединения
                     TCPDUMP FLAGS
Unskilled =  URG  =  (Not Displayed in Flag Field, Displayed elsewhere) 
Attackers =  ACK  =  (Not Displayed in Flag Field, Displayed elsewhere)
Pester    =  PSH  =  [P] (Push Data)
Real      =  RST  =  [R] (Reset Connection)
Security  =  SYN  =  [S] (Start Connection)
Folks     =  FIN  =  [F] (Finish Connection)
          SYN-ACK =  [S.] (SynAcK Packet)
                     [.] (No Flag Set)
```

Отправитель
```
13:26:49.900544 f0:2f:74:ce:fd:0d > 00:15:5d:01:3e:70, ethertype IPv4 (0x0800), length 66: 192.168.1.62.55907 > 192.168.1.23.80: Flags [S], seq 889271057, win 64240, options [mss 1460,nop,wscale 8,nop,nop,sackOK], length 0
13:26:49.900941 00:15:5d:01:3e:70 > f0:2f:74:ce:fd:0d, ethertype IPv4 (0x0800), length 66: 192.168.1.23.80 > 192.168.1.62.55907: Flags [S.], seq 4065700197, ack 889271058, win 64240, options [mss 1460,nop,nop,sackOK,nop,wscale 7], length 0
13:26:49.900941 f0:2f:74:ce:fd:0d > 00:15:5d:01:3e:70, ethertype IPv4 (0x0800), length 54: 192.168.1.62.55907 > 192.168.1.23.80: Flags [.], ack 1, win 8212, length 0
13:26:51.670113 f0:2f:74:ce:fd:0d > 00:15:5d:01:3e:70, ethertype IPv4 (0x0800), length 55: 192.168.1.62.55907 > 192.168.1.23.80: Flags [P.], seq 1:2, ack 1, win 8212, length 1: HTTP
13:26:51.670113 00:15:5d:01:3e:70 > f0:2f:74:ce:fd:0d, ethertype IPv4 (0x0800), length 54: 192.168.1.23.80 > 192.168.1.62.55907: Flags [.], ack 2, win 502, length 0
13:26:51.670113 00:15:5d:01:3e:70 > f0:2f:74:ce:fd:0d, ethertype IPv4 (0x0800), length 381: 192.168.1.23.80 > 192.168.1.62.55907: Flags [P.], seq 1:328, ack 2, win 502, length 327: HTTP: HTTP/1.1 400 Bad Request
13:26:51.670113 00:15:5d:01:3e:70 > f0:2f:74:ce:fd:0d, ethertype IPv4 (0x0800), length 54: 192.168.1.23.80 > 192.168.1.62.55907: Flags [F.], seq 328, ack 2, win 502, length 0
13:26:51.670113 f0:2f:74:ce:fd:0d > 00:15:5d:01:3e:70, ethertype IPv4 (0x0800), length 54: 192.168.1.62.55907 > 192.168.1.23.80: Flags [.], ack 329, win 8211, length 0
13:26:51.671780 f0:2f:74:ce:fd:0d > 00:15:5d:01:3e:70, ethertype IPv4 (0x0800), length 54: 192.168.1.62.55907 > 192.168.1.23.80: Flags [F.], seq 2, ack 329, win 8211, length 0
13:26:51.671780 00:15:5d:01:3e:70 > f0:2f:74:ce:fd:0d, ethertype IPv4 (0x0800), length 54: 192.168.1.23.80 > 192.168.1.62.55907: Flags [.], ack 3, win 502, length 0
```
	
Получатель
```
10:26:49.455227 f0:2f:74:ce:fd:0d > 00:15:5d:01:3e:70, ethertype IPv4 (0x0800), length 66: 192.168.1.62.55907 > 192.168.1.23.80: Flags [S], seq 889271057, win 64240, options [mss 1460,nop,wscale 8,nop,nop,sackOK], length 0
10:26:49.455270 00:15:5d:01:3e:70 > f0:2f:74:ce:fd:0d, ethertype IPv4 (0x0800), length 66: 192.168.1.23.80 > 192.168.1.62.55907: Flags [S.], seq 4065700197, ack 889271058, win 64240, options [mss 1460,nop,nop,sackOK,nop,wscale 7], length 0
10:26:49.455413 f0:2f:74:ce:fd:0d > 00:15:5d:01:3e:70, ethertype IPv4 (0x0800), length 54: 192.168.1.62.55907 > 192.168.1.23.80: Flags [.], ack 1, win 8212, length 0
10:26:51.224605 f0:2f:74:ce:fd:0d > 00:15:5d:01:3e:70, ethertype IPv4 (0x0800), length 55: 192.168.1.62.55907 > 192.168.1.23.80: Flags [P.], seq 1:2, ack 1, win 8212, length 1: HTTP
10:26:51.224682 00:15:5d:01:3e:70 > f0:2f:74:ce:fd:0d, ethertype IPv4 (0x0800), length 54: 192.168.1.23.80 > 192.168.1.62.55907: Flags [.], ack 2, win 502, length 0
10:26:51.224794 00:15:5d:01:3e:70 > f0:2f:74:ce:fd:0d, ethertype IPv4 (0x0800), length 381: 192.168.1.23.80 > 192.168.1.62.55907: Flags [P.], seq 1:328, ack 2, win 502, length 327: HTTP: HTTP/1.1 400 Bad Request
10:26:51.224804 00:15:5d:01:3e:70 > f0:2f:74:ce:fd:0d, ethertype IPv4 (0x0800), length 54: 192.168.1.23.80 > 192.168.1.62.55907: Flags [F.], seq 328, ack 2, win 502, length 0
10:26:51.224996 f0:2f:74:ce:fd:0d > 00:15:5d:01:3e:70, ethertype IPv4 (0x0800), length 54: 192.168.1.62.55907 > 192.168.1.23.80: Flags [.], ack 329, win 8211, length 0
10:26:51.227047 f0:2f:74:ce:fd:0d > 00:15:5d:01:3e:70, ethertype IPv4 (0x0800), length 54: 192.168.1.62.55907 > 192.168.1.23.80: Flags [F.], seq 2, ack 329, win 8211, length 0
10:26:51.227057 00:15:5d:01:3e:70 > f0:2f:74:ce:fd:0d, ethertype IPv4 (0x0800), length 54: 192.168.1.23.80 > 192.168.1.62.55907: Flags [.], ack 3, win 502, length 0
```
