# LAB2
La création d'un AVD:

Application / Version : Android Emulator (API 36 – Android 16.0)
Support : Environnement virtualisé (AVD – Android Virtual Device / Pixel 6)
Objectif : "Comprendre rooting et impacts"
Données : "Fictives"
Réseau : "Test"

![Capture TP 2](1.png)

![Capture TP 2](2.png)

Étape 1 : Rooter l'AVD

![Capture TP 2](3.png)

![Capture TP 2](4.png)

Interprétation des résultats : 
uid=0 = privilèges root confirmés.
L'AVD est en état orange -> l’intégrité du système n’est plus garantie.
adb shell getprop ro.boot.veritymode:
enforcing -> Cela signifie que l’émulateur utilise overlayfs pour permettre les modifications sans casser totalement le système.

Fichier de Journalisation :

![Capture TP 2](5.png)

#Livrable:
1) Définition du rooting 

Le rooting consiste à obtenir les privilèges administrateur (root) sur un appareil Android.
Il permet d’accéder à des zones du système normalement protégées.
Le rooting offre la possibilité de modifier des fichiers système et d’installer des applications avec des droits élevés.
Cependant, il compromet la sécurité native et peut exposer le device à des vulnérabilités et des malwares.

2) Schéma simple : Verified Boot / AVB

Chaîne de confiance : Bootloader(vérifie signature de l'image boot) → Kernel (Android Verified Boot)→ System(vérifie intégrité) → Vendor(vérifie intégrité) → Apps .

Chaque étape vérifie la signature de la précédente pour s’assurer qu’aucune modification non autorisée n’a eu lieu.

3) 8 risques du rooting + 8 mesures défensives


4️⃣ MASVS : 2 exigences résumées
Exigence MASVS	Description courte
MASVS-1	L’application doit protéger les données sensibles en mémoire et sur le stockage
MASVS-2	L’application doit détecter si le device est rooté et réagir en conséquence
5️⃣ MASTG : 2 idées de tests
Test MASTG	Objectif
MASTG-1	Vérifier que l’application ne s’exécute pas sur un device rooté ou avec bootloader unlock
MASTG-2	Tester la résistance aux modifications de fichiers système via overlayfs ou remount
6️⃣ Fiche environnement remplie
Élément	Détails
App testée	DivaApplication.apk
Version	SDK 23 (APK)
Support	AVD API 29+ (rooté)
Objectif	Observer root et protections Verified Boot
Données	Fictives
Réseau	Réseau local de test
