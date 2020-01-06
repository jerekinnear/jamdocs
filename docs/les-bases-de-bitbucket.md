---
categorie: []
title: Les Bases de bitbucket
date: 2020-01-03
slug: bitbucket

---
## **Créer un repository sur Bitbucket**
Si vous voulez restreindre l’accès à certaines parties de vos sites Web en forçant un logon (mot de passe), c’est possible avec [Apache2](http://fr.wikipedia.org/wiki/Apache_HTTP_Server) en créant **un fichier .htaccess et un fichier contenant les utilisateurs autorisés et leurs mots de passe**.

**Les fichiers .htaccess permettent plein de choses. Je ne m’intéresse ici qu’au contrôle d’accès à un dossier. Je vais définir dans .htaccess l’accès par un mot de passe.**

Je me base sur le document « [Apache – Les fichiers .htaccess](http://www.commentcamarche.net/contents/apache/apacht.php3) » en licence [Creative Commons](http://www.commentcamarche.net/contents/ccmguide/ccmlicence.php3), de [Jean-François Pillou](https://www.webactus.net/webmarketing/2967-apache2-mot-de-passe-avec-htaccess/webmaster@commentcamarche.net) et Douglas Six trouvée sur « [Comment ça marche](http://www.commentcamarche.net/)« .

**Je veux restreindre l’accès à mes statistiques** [**Munin**](http://fr.wikipedia.org/wiki/Munin_%28Surveillance_syst%C3%A8me_et_r%C3%A9seau%29)**, et forcer un logon.**

**Je dois créer un fichier .htaccess qui contiendra l’indication qu’il faut un logon, et l’endroit où se trouve le fichier de mot de passe, et ensuite, créer ce fichier avec la liste des utilisateurs autorisés et leurs mots de passe.**

**Le fichier .htaccess doit se trouver dans le dossier Web concerné**, donc ici dans mon dossier Munin (adaptez en fonction de votre configuration et de vos dossiers).

    $ cd /var/www/munin

Voici son contenu :

    #ErrorDocument 403 http ://www.misson.net/accesrefuse.php3
    AuthUserFile /home/didier/sites-htpasswd/munin
    AuthGroupFile /dev/null
    AuthName "Restricted Access (Didier Misson)"
    AuthType Basic
    <LIMIT GET POST>
    
    Require valid-user
    </LIMIT>

La première ligne, en commentaire dans mon cas, vous permet éventuellement de personnaliser votre message d’erreur en cas d’erreur d’accès.

La ligne « AuthName » contient le texte qui sera affiché dans la fenêtre de logon.

Le « Require valid-user » précise qu’il faut obligatoirement un user valide … et son mot de passe !

**Il faut indiquer où se trouve cette liste d’utilisateur autorisé.**

Si vous avez un hébergement chez un fournisseur, vous n’avez peut-être pas le choix de l’endroit ! Vous serez probablement obligé de laisser cette liste de mots de passe dans votre dossier web. Dans ce cas, vous pourriez simplement l’appeler « .htpasswd ».

Si vous avez votre propre serveur à la maison, ou un serveur dédié, il est préférable de ne pas mettre le fichier mots de passe dans le dossier Web.

Je me suis créé un dossier /home/didier/sites-htpasswd où je mets les différents fichiers mots de passe pour Apache.

**Création du fichier mots de passe et ajout d’utilisateurs.**

Je vais donc dans mon dossier /home/didier/sites-htpasswd :

    $ cd /home/didier/sites-htpasswd/

La configuration de base d’Apache suppose que les mots de passe sont codés en [MD5](http://fr.wikipedia.org/wiki/Md5).

**Une commande est prévue pour créer ce fichier : « htpasswd »**

Le flag » -c » permet de créer le fichier mots de passe. Il faut l’utiliser la première fois.

Il faut également préciser le nom du fichier mots de passe, et le userid que vous voulez ajouter :

     :/home/didier/sites-htpasswd$ htpasswd -c munin didier
    New password :
    Re-type new password :
    Adding password for user didier

Pour les utilisateurs suivants, il ne faut plus mettre le » -c » :

     :/home/didier/sites-htpasswd$ htpasswd munin maurice
    New password :
    Re-type new password :
    Adding password for user maurice
     :/home/didier/sites-htpasswd$ htpasswd munin kevin
    New password :
    Re-type new password :
    Adding password for user kevin

**Que contient le fichier généré ?**

     :/home/didier/sites-htpasswd$ cat munin
    didier :5jOSjJmQhKrng
    maurice :DQbxW83DfGtUw
    kevin :bpghOeADgxX.U

Les mots de passe sont chiffrés. En fait, ils ne sont pas réellement dans le fichier, mais c’est leur signature MD5 qui est sauvée.

Lors du logon, Apache2 va calculer le code MD5 du mot de passe que vous avez introduit, et le comparer avec le contenu du fichier.

**Le logon, avec Opera (pour changer… il n’y a pas que Firefox sous Linux) :**

Si vous n’êtes pas autorisé à entrer sur ce site (ou si vous tapez un mauvais mot de passe), le site Web redemande le mot de passe, sauf si vous cliquez sur « Annuler ». Vous auriez alors ce message d’erreur (ou celui que vous avez personnalisé !) :

**_Authorization Required_**

**_This server could not verify that you are authorized to access the document requested. Either you supplied the wrong credentials (e.g., bad password), or your browser doesn’t understand how to supply the credentials required._**

**Si vous devez supprimer un utilisateur de la liste des personnes autorisées**, évidemment vous pourriez éditer le fichier et supprimer la ligne de cet utilisateur. Mais c’est possible aussi avec la commande « htpasswd » :

     :/home/didier/sites-htpasswd$ htpasswd -D munin maurice
    Deleting password for user maurice
     :/home/didier/sites-htpasswd$ cat munin
    didier :5jOSjJmQhKrng
    kevin :bpghOeADgxX.U

**Voilà, l’utilisateur « maurice » est supprimé.**
