<div align="center"><H1> Deployment -  WDS </H1></div>

# Prérequis

Mettre l'ISO d'une image Windows dans le lecteur DVD du serveur. Par exemple l'ISO de Windows Server 2022

# Image de démarrage

Ouvrir la console de gestion WDS.

> Sélectionner le serveur WDS et dérouler l'arborescence de dossiers en dessous  
> Faire un clic droit sur le dossier **Boot Images** et cliquez sur **Add Boot Image**  
> Aller chercher dans le lecteur DVD, dans le dossier **sources**, sélectionner le fichier **Boot.wim**, cliquer sur **Open** puis **Next**  
> Dans la fenêtre **Image Et data** tu peux changer le nom proposé par défaut pour l'image de démarrage

Dans le dossier **Boot Images** on peut voir dans la fenêtre de droite l'image ajoutée :  

![9_BOOT_IMAGES.png](https://github.com/Skchaper/WDS/blob/main/SCREENS/9_BOOT_IMAGES.png)



# Image d'installation

