
<div align="center"><H1> Install -  WDS </H1></div>

# Prérequis

- VM Microsoft Windows Server 2022 :

>  Adresse IP fixe du serveur : 192.168.10.2/24  
>  Nom du serveur : srv-wds  

- Ce serveur est installé avec le rôle DHCP dans la configuration suivante :

> Début de plage d'adresses : 192.168.10.10  
> Fin de plage d'adresses : 192.168.10.100  
> Masque : /24  

- Ce serveur dispose de 2 disques configurés comme ceci :

Disque système : 30 Go  

Disque WDS :  
> Taille de volume : 30 Go  
> Partition de type : GPT  
> File system : NTFS  
> Nom : WDS  

# WDS en PowerShell

**Installation du rôle WDS**

```
Install-WindowsFeature wds-deployment -includemanagementtools
```

![1_INSTALLATION_R%C3%94LE_WDS.png](https://github.com/Skchaper/WDS/blob/main/SCREENS/1_INSTALLATION_R%C3%94LE_WDS.png)

**Configuration du WDS**

Taper la commande suivante pour configurer le service :

```
wdsutil /Initialize-Server /Server:srv-wds /remInst:D:\WdsData /Standalone
```

Exécuter la commande suivante pour configurer la gestion des clients :

```
wdsutil /Set-Server /Server:srv-wds /AnswerClients:All
```

La commande suivante va permettre de vérifier la configuration :

```
wdsutil /Get-Server /Server:srv-wds /Show:Config
```

![2_CONFIGURATION_WDS.png](https://github.com/Skchaper/WDS/blob/main/SCREENS/2_CONFIGURATION_WDS.png)

**Lancement du service WDS**

```
Start-Service -Name WDSServer
```

L'icone verte sur le nom du serveur montre que le service est lancé :  
![3_LANCEMENT_SERVICE.png](https://github.com/Skchaper/WDS/blob/main/SCREENS/3_LANCEMENT_SERVICE.png)


# WDS en mode graphique

**Installation du rôle WDS**

> Ouvrir le **Service Manager**
> Aller dans **Manage** puis **Add Roles and Features**  
> Cliquer sur **Next**  
> Sélectionner **Role-based or feature-based installation** puis **Next**  
> Sélectionner votre serveur et cliquer sur **Next**  
> Choisir le rôle **Windows Deployment Services**, dans la fenêtre qui apparaît cliquer sur **Add features**  
> Cliquer 4 fois sur **Next** en laissant les options par défaut  
> Cliquer sur **Install puis Close**  

L'installation est terminée lorsque le rôle **WDS** apparaît dans le **Server Manager** :  
![4_WDS_SERVER_MANAGER.png](https://github.com/Skchaper/WDS/blob/main/SCREENS/4_WDS_SERVER_MANAGER.png)

**Configuration du WDS**

Lancer la console WDS, taper la commande suivante dans PowerShell :

```
WdsMgmt.msc
```

La fenêtre suivante s'ouvre :
![5_FEN%C3%8ATRE_WDS.png](https://github.com/Skchaper/WDS/blob/main/SCREENS/5_FEN%C3%8ATRE_WDS.png)

> Cliquer sur le nœud Servers  
> Sélectionner le serveur WDS et cliquer avec le bouton droit de la souris  
> Sélectionner Configure Server, cette fenêtre apparait :  

![6_CONFIGURE_SERVER.png](https://github.com/Skchaper/WDS/blob/main/SCREENS/6_CONFIGURE_SERVER.png)

Le reste des pré-requis est bon :  

> Serveur DHCP, ici le service DHCP est sur le même serveur  
> Pas de rôle DNS  
> Partition NTFS réservée pour le stockage des images  



**Lancement du service WDS**
