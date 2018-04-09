<!-- TITLE: Vagrant -->
# Introduction
## Qu'est ce que c'est ?
**Vagrant** vous permet de construire et gérer des machines virtuelles facilement. Il utilise un *provider* en backend (typiquement VirtualBox) pour toute la partie virtualisation.
Vous pouvez vous representez **Vagrant** comme un *wrapper* autour de VirtualBox (par exemple).

Pour plus d'informations: [Introduction to Vagrant](https://www.vagrantup.com/intro/index.html)

## Différences avec Docker ?
**Docker** crée des containers single-application. **Vagrant** crée des machines virtuelles.
L'utilisation de l'un ou l'autre dépendra de votre besoin.

Sur les Macs de l'école, utiliser l'un ou l'autre ne change pas grand chose.
**Docker** nécessitant des features du Kernel Linux pour fonctionner, il doit lancer une machine virtuelle exécutant une distribution Linux légère (*boot2docker* ou *Alpine*) pour ensuite exécuter le daemon **Docker** dedans. C'est ce qu'automatise `docker-machine` pour vous si vous n'utilisez pas *Docker for Mac*.

## Comment l'installer ?
**Vagrant** et **VirtualBox** sont disponible dans le *Managed Software Center*.

## Comment s'en servir à l'école ?
On va commencer par changer l'emplacement de stockage des machines virtuelles car les sessions sont limités à 4Go.

Vous avez 2 choix pour le stockage:
- `/Volumes/Storage/goinfre/<login>`
- `~/sgoinfre`

### Choix #1: `/Volumes/Storage/goinfre/<login>`
Avantages:
- local à votre Mac, donc les meilleures performances possible
- Force les VMs à être *stateless*

Inconvénients:
- Vos VMs étant local au Mac sur lequel vous travaillez, si vous changez de Mac vous n'aurez pas vos VMs sur le nouveau Mac

### Choix #2: `~/sgoinfre`
Avantages:
- Stockage distant (NFS de l'école), donc vos VMs ne sont jamais perdus.

Inconvénients:
- Stockage distant, donc performance moindre voir catastrophique
- Force les VMs à ne plus être *stateless*

### Changer l'emplacement de stockage
Vous avez choisis votre méthode de stockage? Parfait! Maintenant comment l'indiquer à **Vagrant** et **VirtualBox** ?

Pour **Vagrant** il faut ajouter une variable d'environnement, `VAGRANT_HOME`, qui spécifie l'emplacement de stockage.
Si vous choisissez le stockage en local sur le Mac (ProTip: je vous le recommande), exécutez ces commandes:
``` bash
mkdir /Volumes/Storage/goinfre/$USER/vagrant
echo 'export VAGRANT_HOME=/Volumes/Storage/goinfre/$USER/vagrant' >> ~/.zshrc
```

Pour **VirtualBox** suivez [ce guide en image](http://www.thisprogrammingthing.com/2013/changing-the-directory-vagrant-stores-the-vms-in/), ce sera plus simple.
N'oubliez pas d'adapter l'emplacement de stockage. Par exemple pour du stockage en local: `/Volumes/Storage/goinfre/$USER/virtualbox`
