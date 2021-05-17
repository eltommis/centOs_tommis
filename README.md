# CENTOS
La macchina virtuale su cui ho installato i vari servizi, utilizza come sistema operativo Centos 7. Ho deciso di utilizzare come editor di testo nano.
<br>
![Inizio](https://user-images.githubusercontent.com/77326242/118560350-a43f6800-b769-11eb-8cef-197d74641445.png)

# SSH
Successivamente ho installato il protocollo SSH, che permette di stabilire una sessione remota cifrata tramite interfaccia a riga di comando con un altro host di una rete informatica; per installarlo e configurarlo  ho utilizzato i comandi:
- sudo yum install sshd
- systemctl start sshd
- systemctl enable sshd
<br> ![SSH_INSTALLAZIONE](https://user-images.githubusercontent.com/77326242/118560363-ab667600-b769-11eb-94f4-b5bd0d4806cd.png)
<br>
Sono stati modificati all'interno di /etc/ssh/sshd_config i permessi impedendo l'accesso da remoto all'utente root e, inoltre, sono stati indicati gli utenti che possono accedere da remoto.

<br>![PERMESSI_SSH](https://user-images.githubusercontent.com/77326242/118560380-b0c3c080-b769-11eb-8b44-6fe43c5a6e9f.png)



# HTTP
E' stato installato e configurato il servizio http tramite i comandi:
- yum install httpd
- systemctl start httpd
- systemctl enable httpd
 * 167 *
E' stato configurato un firewall per permettere l'accesso alla porta di default del servizio (80/tcp) ed è stato effettuato un 
ricaricamento delle impostazioni 


# PhpMyAdmin
è stato installato il repo aggiuntivo EPEL repo tramite il comando:
- yum install epel-release
in seguito è stato installato  phpMyAdmin con il comando:
- yum install phpmyadmin
 * 171 *
E' stato modificato il file di configurazione /etc/httpd/conf.d/phpMyAdmin.conf impostando un alias personalizzato:
- #Alias /phpmyadmin /usr/share/phpMyAdmin
- #Alias /phpMyAdmin /usr/share/phpMyAdmin
- Alias /<mio_alias> /usr/share/phpMyAdmin<br>
177 

# FTP
E' stato installato il servizio FTP, protocollo di livello applicazioni per la trasmissione dei dati tra host basato su TCP 
e con architettura di tipo client-server.
I comandi che sono stati digitati per l'installazione sono:
- yum install vsftpd
- systemctl start vsftpd
- systemctl enable vsftpd
180
181
sono stati impostati i firewall:
- firewall-cmd --permanent --add-service=ftp
- firewall-cmd --reload
182
Per rendere più sicuro il servizio e permettere l'accesso ai soli utenti di sistema si è deciso di:
- impedire accesso utenti anonimi
- abilitare il chroot'ing (chroot jail)
- permettere agli utenti locali di poter scrivere nella propria home dir
* 183 *
* 184 *
