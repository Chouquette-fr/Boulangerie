# iForensics-iCrash 

###### Contexte : 
Lors d’un passage de douane, le douanier vous demande de lui remettre votre téléphone ainsi que son code de déverrouillage. Le téléphone vous est rendu quelques heures plus tard …

Suspicieux, vous envoyez votre téléphone pour analyse au CERT-FR de l’ANSSI. Les analystes du CERT-FR effectuent une collecte sur le téléphone, composée d’un sysdiagnose et d’un backup.

Il semblerait qu’un flag se soit caché à l’endroit où sont stockés les crashes sur le téléphone …

Cette épreuve fait partie d’une série. Les épreuves sont indépendantes sauf iBackdoor 2/2 qui dépend de iBackdoor 1/2 :

iForensics - iCrash
iForensics - iDevice
iForensics - iWiFi
iForensics - iTreasure
iForensics - iNvisible
iForensics - iBackdoor 1/2
iForensics - iBackdoor 2/2
iForensics - iC2
iForensics - iCompromise

###### Résolution : 

Pour ce challenge, nous avons accès à deux archives : backup.tar.xz et sysdiagnose_and_crashes.tar.xz. 

Nous savons que le flag est caché ou sont stocké les crashes sur le téléphone. Nous nous intéressons donc naturellement à l'archive sysdiagnose_and_crashes.tar.xz. 

1. Création d'un répértoire de travail
   
Je créer un répertoire dans lequel je vais extraire l'archive.
> `mkdir sysdiagnose`

2. Extraction de l'archive
   
J'extrai ensuite l'archive dans le répertoire de travail.
> `tar -xvf sysdiagnose_and_crashes.tar.xz -C ./sysdiagnose`

3. Là où sont les crashes

Nous allons ensuite naviguer à l'endroit ou sont stocké les crashes.
> `cd /sysdiagnose/private/var/mobile/Library/Logs/CrashReporter`

En affichant le contenu de ce dossier, nous pouvons apercevoir un fichier txt intéressant : **fcsc_intro.txt** 
> `ls`
![contenu de CrashReporter]()

4. Flag
   
En affichant le contenu de **fcsc_intro.txt** nous avons directement accès au flag.
> `cat fcsc_intro.txt`
Flag :*FCSC{7a1ca2d4f17d4e1aa8936f2e906f0be8}*



