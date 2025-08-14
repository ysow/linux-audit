# linux-audit

## 📌 Objectif
Configurer un serveur web sécurisé avec Nginx, HTTPS et sauvegarde automatisée des logs.

## 🛠️ Prérequis
- [ ] Compte cloud (Scaleway, AWS, GCP ou VM locale)
- [ ] OS : Debian 12 ou Ubuntu 22.04
- [ ] Droits sudo
- [ ] Accès SSH

## 🚀 Étapes

### 1. Déploiement de la VM
[Commandes ou étapes pour créer la VM]

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
