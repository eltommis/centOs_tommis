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

<br> ![PERMESSI_SSH](https://user-images.githubusercontent.com/77326242/118560380-b0c3c080-b769-11eb-8b44-6fe43c5a6e9f.png)



# HTTP
E' stato installato e configurato il servizio http tramite i comandi:
- yum install httpd
- systemctl start httpd
- systemctl enable httpd

<br> ![InstallazioneHttp](https://user-images.githubusercontent.com/77326242/118561431-3eec7680-b76b-11eb-8aab-f16656475c31.png)
<br>
E' stato configurato un firewall per permettere l'accesso alla porta di default del servizio (80/tcp) ed è stato effettuato un ricaricamento delle impostazioni

<br> ![FirewallPorta](https://user-images.githubusercontent.com/77326242/118561482-562b6400-b76b-11eb-977b-ef09fba6044a.png)
<br>


# PhpMyAdmin
è stato installato il repo aggiuntivo EPEL repo tramite il comando:
- yum install epel-release
in seguito è stato installato  phpMyAdmin con il comando:
- yum install phpmyadmin

<br> ![PhpMyAdmin_INstallazione](https://user-images.githubusercontent.com/77326242/118562326-c5ee1e80-b76c-11eb-98f9-9e79882a0a00.png)
<br>
E' stato modificato il file di configurazione /etc/httpd/conf.d/phpMyAdmin.conf impostando un alias personalizzato:
- #Alias /phpmyadmin /usr/share/phpMyAdmin
- #Alias /phpMyAdmin /usr/share/phpMyAdmin
- Alias /<mio_alias> /usr/share/phpMyAdmin<br>

<br>![Alias](https://user-images.githubusercontent.com/77326242/118562343-cc7c9600-b76c-11eb-8b5f-9380447d987f.png)
<br>

# FTP
E' stato installato il servizio FTP, protocollo di livello applicazioni per la trasmissione dei dati tra host basato su TCP 
e con architettura di tipo client-server.
I comandi che sono stati digitati per l'installazione sono:
- yum install vsftpd
- systemctl start vsftpd
- systemctl enable vsftpd

<br>![FTP_Installazione](https://user-images.githubusercontent.com/77326242/118563499-f6cf5300-b76e-11eb-902e-18e6250b480e.png)
<br>

<br>![FTP_Ctl](https://user-images.githubusercontent.com/77326242/118563508-fa62da00-b76e-11eb-963e-b0e6e61eeb6d.png)
<br>
sono stati impostati i firewall:
- firewall-cmd --permanent --add-service=ftp
- firewall-cmd --reload

<br>![FirewallFtp](https://user-images.githubusercontent.com/77326242/118563535-064e9c00-b76f-11eb-93e5-baad78c807e4.png)
<br>

Per rendere più sicuro il servizio e permettere l'accesso ai soli utenti di sistema si è deciso di:
- impedire accesso utenti anonimi
- abilitare il chroot'ing (chroot jail)
- permettere agli utenti locali di poter scrivere nella propria home dir

<br>![UtentiAccesso](https://user-images.githubusercontent.com/77326242/118563559-0fd80400-b76f-11eb-843c-c441025f2451.png)
<br>

<br>![UtentiAccesso2](https://user-images.githubusercontent.com/77326242/118563576-16667b80-b76f-11eb-8554-439e45b88027.png)
<br>
