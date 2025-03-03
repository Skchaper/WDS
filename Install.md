
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

```
Install-WindowsFeature wds-deployment -includemanagementtools
```

# WDS en mode graphique
