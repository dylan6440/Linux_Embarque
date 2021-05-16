# Création d'une recette et utilisation de YOCTO pour RPI3

Ajout des layers modification du local.conf pour ajouter la machine
    
![bblayers](https://user-images.githubusercontent.com/70941138/118407609-c9f14200-b681-11eb-8f81-660b20c19cd6.PNG)
![localconf](https://user-images.githubusercontent.com/70941138/118408044-f5752c00-b683-11eb-91da-19215ba44979.PNG)


J'ai ensuite suivi les consignes suivantes :

![instruction](https://user-images.githubusercontent.com/70941138/118407988-c5c62400-b683-11eb-8dca-21ef2db35888.PNG)

et j'ai créé / modifié les documents demandés

![imagebb](https://user-images.githubusercontent.com/70941138/118408002-d7a7c700-b683-11eb-97dc-781d4f45d475.PNG)
![helloc](https://user-images.githubusercontent.com/70941138/118408007-dd9da800-b683-11eb-9711-b2e7df969d0a.PNG)
![hellobb](https://user-images.githubusercontent.com/70941138/118408010-deced500-b683-11eb-9308-da59197836e9.PNG)

lancement du build

![build](https://user-images.githubusercontent.com/70941138/118411269-f3b36480-b693-11eb-8c62-4627c975b134.PNG)

Une fois le build fini, j'ai voulut copié l'image present dans le dossier tmp/deploy/images/ sur ma MicroSD pour mettre sur ma rpi3. 

        $ dd if=MonImage.rootfs.rpi-sdimg of=/dev/sdb bs=4M


Ma vm a planté et impossible de me relog ou de recupérer les documents.
J'ai essayé de me relog même avec le terminal de secours, créé un newuser et impossible quand même d'avoir accés a mes fichier.
![login](https://user-images.githubusercontent.com/70941138/118411763-7ccb9b00-b696-11eb-92c4-3b861022f564.PNG)

j'ai donc recréé une vm, refaits toute les installations mais je n'ai pus rendre le tp fini a temps.
