# linux-audit

## 📌 Objectif
Configurer un serveur web sécurisé avec Nginx, HTTPS et sauvegarde automatisée des logs.

## 🛠️ Prérequis
- [ ] Compte cloud (Scaleway, AWS, GCP ou VM locale)
- [ ] OS : Debian 12 ou Ubuntu 22.04
- [ ] Droits sudo
- [ ] Accès SSH

## 🚀 Étapes

### 1. Audit de la VM 
```bash
# Nom et version
hostnamectl

# Uptime et charge
uptime

# Version du kernel
uname -a

# Espace disque
df -h

# Utilisation mémoire
free -h
```

### 2. Configuration de l’utilisateur
```bash
# Créer utilisateur
sudo adduser devops
sudo usermod -aG sudo devops
```
### 3. Sécurisation SSH
```bash
# Sauvegarde de la config
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak

# Modifier la config pour :
# - Interdire root login
# - Changer port SSH
sudo nano /etc/ssh/sshd_config
# Port 2222
# PermitRootLogin no

sudo systemctl restart ssh
```
### Configuration de Firewall
```bash

devops@scw-adoring-driscoll:/home/ubuntu$ sudo apt install ufw -y
[sudo] password for devops: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
ufw is already the newest version (0.36.2-6).
ufw set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 56 not upgraded.
devops@scw-adoring-driscoll:/home/ubuntu$ sudo ufw allow 2222/tcp
Rules updated
Rules updated (v6)
devops@scw-adoring-driscoll:/home/ubuntu$ sudo ufw allow 80/tcp
Rules updated
Rules updated (v6)
devops@scw-adoring-driscoll:/home/ubuntu$ sudo ufw enable
Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
Firewall is active and enabled on system startup
devops@scw-adoring-driscoll:/home/ubuntu$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
2222/tcp                   ALLOW       Anywhere                  
80/tcp                     ALLOW       Anywhere                  
2222/tcp (v6)              ALLOW       Anywhere (v6)             
80/tcp (v6)                ALLOW       Anywhere (v6)             

```
