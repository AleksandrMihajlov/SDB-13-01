# SDB-13-01
Уязвимости и атаки на информационные системы - Aleksandr Mihajlov SYS34  
  
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
  
- Службы (скриншот 1.1)  
- CVE-2011-2523 ftp-vsftpd-backdoor (Скриншот 2.2) https://vulmon.com/vulnerabilitydetails?qid=CVE-2011-2523  
- CVE-2010-4344 smtp-vuln-cve2010-4344 (Скриншот 3.3) https://vulmon.com/vulnerabilitydetails?qid=CVE-2010-4344  
- CVE-2015-4000 ssl-dh-params (Скриншот 4.4) https://vulmon.com/vulnerabilitydetails?qid=CVE-2015-4000  
- CVE-2007-6750 http-slowloris-check (Скриншот 5.5) https://vulmon.com/vulnerabilitydetails?qid=CVE-2007-6750  
- CVE-2014-3566 ssl-poodle (Скриншот 6.6) https://vulmon.com/vulnerabilitydetails?qid=CVE-2014-3566  
  
Скриншоты  
<details>   

![alt text](https://github.com/AleksandrMihajlov/SDB-13-01/blob/main/1.1.PNG)  

![alt text](https://github.com/AleksandrMihajlov/SDB-13-01/blob/main/2.2.PNG)  

![alt text](https://github.com/AleksandrMihajlov/SDB-13-01/blob/main/3.3.PNG)  

![alt text](https://github.com/AleksandrMihajlov/SDB-13-01/blob/main/4.4.PNG)  

![alt text](https://github.com/AleksandrMihajlov/SDB-13-01/blob/main/5.5.PNG)  

![alt text](https://github.com/AleksandrMihajlov/SDB-13-01/blob/main/6.6.PNG)  

</details>  
  
### Задание 2

Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.

Запишите сеансы сканирования в Wireshark.

Ответьте на следующие вопросы:

- Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?
- Как отвечает сервер?

*Приведите ответ в свободной форме.*  
  
- Используются разные протоколы, которые взаимодействуют с портами устройства и генерируют раздичные типы трафика.  
  
- SYN
Отправка TCP-SYN  
Получаем ответ SYN/ACK порт открыт, готов к соединению.  
Получаем ответ RST, порт закрыт.  
Ответ не пришел, порт фильтруется.  
  
- FIN
Отправка TCP-FIN  
При не активном соединении, получаем RST для сброса соединения.  
  
- Xmac  
Отправка TCP-FIN,PSH,URG  
Получаем ответ RST, порт закрыт.  
Ответ не пришел, порт фильтруется.  
  
- UDP  
Отправка пустого UDP  
Получаем ответ "port unreachable", порт азкрыт.  
Получаем ответ на запрос, порт открыт.  
Ответ не пришел, порт открыт или фильтруется.

