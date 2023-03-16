Pour Apache 
------------------------------
cd /etc/apache2
nano apache2.conf 

<Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
        Header set Access-Control-Allow-Origin "*"
</Directory>

cd /etc/apache2
cd sites-enabled
nano 000-default.conf

 ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html
        Header set Access-Control-Allow-Origin "*"

cd /etc/apache2
cd sites-available
nano 000-default.conf

 ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html
        Header set Access-Control-Allow-Origin "*"

cd /etc/apache2
nano ports.conf 

Listen 80

<IfModule ssl_module>
        Listen 443
</IfModule>

<IfModule mod_gnutls.c>
        Listen 443
</IfModule>

Pour Samba
-------------------------------	
cd /etc/samba
nano smbd.conf

interfaces = 127.0.0.0/8 eth0
bind interfaces only = yes

[PartageVM]
        path = /var/www/html
        comment = Partage Samba du dossier html
        writable = yes
        guest ok = no
        guest only = no
        create mode = 0777
        directory mode = 0777
        share modes = yes

systemctl restart apache2
systemctl restart smbd
------------------------------
Erreur de redirection 

cd var/www/
fichier index .... à supprimer 

rm + non du fichier 

Sur le site web retourner sur la page precedente puis ctrl F5 
