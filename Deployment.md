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

Ouvrir la console de gestion WDS.

> Sélectionner le serveur WDS et dérouler l'arborescence de dossiers en dessous  
> Faire un clic droit sur le dossier **Install Images** et cliquez sur **Add Install Image**  
> Dans la fenêtre **Image Group** on doit créer un groupe d'images. Donner un nom de groupe et cliquer sur **Next**  
> Aller chercher dans le lecteur DVD, dans le dossier **sources**, sélectionner le fichier **install.wim**, cliquer sur **Open** puis **Next**  
> Dans la fenêtre **Available Image** tu as la liste de toutes les images d'OS contenues dans le fichier WIM  
> Sélectionne celle(s) que tu veux et clique sur **Next**  

_Il est possible de garder plusieurs images d'installation. Dans tous les cas, il vaut mieux décocher la case **Use the default name and description for each of the selected images**. En effet, il vaut mieux renommer les images pour qu'elles correspondent au besoin. Par exemple, il peut y avoir une image pour le service Comptabilité, une pour la production, etc._ 

> Si la case **Use the default name and description for each of the selected images** est cochée, la fenêtre **Image Data** apparaît. On peut y modifier le nom de l'image et sa description.  
> Cliquer 2 fois sur **Next** puis **Finish**  

> En sélectionnant le dossier **Install Images** tu vois dans la fenêtre de droite le groupe d'images que tu as crée.  
> En cliquant sur celui-ci, tu peux voir l'image d'installation.  

![10_INSTALL_IMAGES.png](https://github.com/Skchaper/WDS/blob/main/SCREENS/10_INSTALL_IMAGES.png)

# Lancement du déploiement

## Prérequis

Démarrer la VM cliente et modifier l'ordre de boot pour qu'elle démarre sur le réseau

## Déploiement

> Le déploiement se fait sous forme graphique.  
> Un compte pour se connecter au serveur est demandé sous la forme **domaine\utilisateur**.  
> Pour le **nom du domaine**, utiliser le nom du serveur WDS.  
> Pour le **compte d'utilisateur**, utiliser le compte d'administration utilisé pour configurer le serveur WDS.  

_Dans ce cas précis on utilise le compte **Administrator** du serveur, mais on peut utiliser un autre compte, à partir du moment où il est autorisé à déployer avec WDS.  
De même, si un domaine était en place, on utiliserai son nom au lieu du nom du serveur WDS._  

Ensuite suivre les indications à l'écran pour déployer le système sur la VM.  

Le système s'installe alors par le réseau.  
Comme l'image n'est pas configurée, des opérations manuelles supplémentaires sont nécessaires  





