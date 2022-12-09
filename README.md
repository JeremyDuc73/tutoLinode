mdp user php : votremdp


SITE: 
ssh ...
apt update
apt upgrade
apt install neovim
apt install apache2
ufw allow 'OpenSSH'
ufw allow 'Apache'
ufw allow 'Apache Full'
ufw enable
tests HTML/CSS
/etc/apache2
freenom :
	- prendre un nom de domaine
	- outil de gestion -> personnalisé -> https://www.linode.com/community/questions/19221/how-to-configure-a-domain-name-step-by-step-on-a-linode-server-platform

créer un domaine avec url et email sur linode
faire deux A records un avec ip et l'autre avec www + ip (ip de la linode)

modifier le fichier dans sites-enabled/
	-> adresse mail
	-> servername
	-> server alias

a2dissite 000-default.conf
systemctl reload apache2
snap install certbot --classic
modifier le fichier ssl (default-ssl.conf)
	-> adresse mail
	-> servername
	-> server alias
	
a2ensite default-ssl.conf
a2ensite 000-default.conf
systemctl reload apache2

certbot --apache

installer githubCLI :

type -p curl >/dev/null || sudo apt install curl -y
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
&& sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& sudo apt update \
&& sudo apt install gh -y

gh auth login
clone le dépot avec la commande


si besoin :
	-> reconfigurer les deux fichiers conf dans sites-available
	-> changer document root
	-> a2ensite & systemctl reload apache2


apt install mysql-server
mysql -u root
changer le mdp mySQL : 
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'votremdpSQL';
mysql_secure_installation

apt install phpmyadmin -> cocher apache2 avec espace
-> ok, puis mettre mdp
apt install php libapache2-mod-php
