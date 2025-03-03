
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

**Lancement du service WDS**

```
wdsutil /Set-Server /Server:srv-wds /AnswerClients:All
```

# WDS en mode graphique
