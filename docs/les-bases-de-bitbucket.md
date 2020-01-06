---
categorie: []
title: Les Bases de bitbucket
date: 2020-01-03
slug: bitbucket

---
**Créer un repository sur Bitbucket**![](https://lh4.googleusercontent.com/idMhKaSiLT1lUSfXL3e_JDK_fo_l08CU70lVMK_ccJluD6S_wNqL2MblrqppduVwjvg35u95zx4WWxb_FOwq8fG0oyNGkrNkb86QR3pDq-bIL8dDYn_3KPHSCHOFSgGjZf__fi8 =30x29)

1️⃣ Dans Bitbucket, cliquer sur l’onglet « create » ![](https://docs.google.com/drawings/u/0/d/s5R9K24rBuG8kxkBqMM43zQ/image?w=461&h=339&rev=1&ac=1&parent=1zyZME-5Xv7Jo-bwoLICPzKyH3aDyImoe =461x339)

2️⃣ Puis cliquer sur sur l’onglet « Repository »

  
![](https://docs.google.com/drawings/u/0/d/shsRVSO4R71pH12ydlPdGvA/image?w=413&h=278&rev=1&ac=1&parent=1zyZME-5Xv7Jo-bwoLICPzKyH3aDyImoe =413x278)

3️⃣ **Ajouter les informations du nouveau répertoire** ![](https://docs.google.com/drawings/u/0/d/skU5ZCD5lQ0rh0Z1OYi_oeg/image?w=567&h=432&rev=1&ac=1&parent=1zyZME-5Xv7Jo-bwoLICPzKyH3aDyImoe =567x432)

# **Ajouter un projet existant au repository vierge**

**ATTENTION : Ne pas faire ceci sur des dossiers en production**

Se rendre à la racine du projet

Créer le fichier ._gitignore_ (._idea_, _vendor_, _node_modules_, _cache_, _uploads,_ _etc_.). Des ._gitignore_ de base se trouvent facilement dans la documentation des outils ou sur le web.

Initialiser git :

git init

![](https://lh4.googleusercontent.com/zCaQ5GHuLyilNTq9AjfcgvK9CTcRH4cy1PUnftMY2jJb7nRrseHvj013tQrkkOFo_m2gU3pJR9qHaKi1nYvhKxi0c6F-8KUI4rhOVLg39g9bBa2ymk4iD7j0ahCVi6NWBVBhAT8 =439x42)

Créer le lien avec le repository git :

Ces infos se trouvent sur le repo vierge dans bitbucket :

![](https://lh5.googleusercontent.com/58DApNq0H1418NejBIFN5npZsS-P-nuvTk3sfhSLBssH_1gspRw7nsg9BY8Ryrlgg-M8yN586IuNmarpzhi6zJ41q3Xp2ia5GR7Bu9v-NYefFF-lyQ-sPMSiDRW1lgIFn04dX6Q =605x611)

git remote add origin <lien du repo>

![](https://lh3.googleusercontent.com/xKGJ4Qoyob8Y2t5_pQ3JrPWYCZH49ls5vR65hDVx6WTzw2Ln2yUWfVdiNWD7tHJsN4iDFq0Z8IHnRzieSp-iMM20eejTmzlcoFYaRJpuuWPjgwsYJVuFHa-YWA_QX5_eypZn-2o =605x26)

Ajouter les fichiers au git

git add .

![](https://lh4.googleusercontent.com/DSNgZxbHIdP54Sa20SQOB8oHCtHKHEFDqFTT7DAFylbww4nzcKFA5JEK_KXOPCuKhZIbgGOvt3DqV3fwp4JVTwGkV701bAvk7trbo5gPPX3f4x_rv_O19TLWgPZWDtKUhj9R6P8 =222x25)

Commit les fichiers

git commit -m « first commit »

![](https://lh5.googleusercontent.com/ecclKWkDI1WSQvxMDULOVK8tE4b6fBeMYLiWKsC49EbeTktx4CDiATo5G829rckdBMTgTo-hiIWEXqEPr-YwCtv2-IEX-nF8NUlv2OZFWRksV9rG_u82cN6oxqeY7C6JhrMnFOw =502x112)

Pousser le commit sur le repo en ligne

git push -u origin master (ou branche concernée)

![](https://lh6.googleusercontent.com/GGhtDpF-1H331rhiElwGcd5765XR6mXCrMI7KM-xzdqp-qfj6YAkbq7K4aORWwlFShJ61vLC0cTj0EO8eNNEmuMv3XqVZ09tJvN8X2-igYuy-kf2RBzx_a438-cHpx5CI0dMT-U =564x213)

# **Cloner un repo**

## En local

git clone https://<username>@<url>

Ici on met le username pour faire le lien avec l’utilisateur qui fait les modifs (donc le votre)

## En ligne

git clone https://<url>

Ici on ne met **pas** le username car on ne doit pas lier à l’utilisateur. L’utilisateur qui clone ne doit pas être le seul à pouvoir faire des pull sur le serveur.

# **Modifier un remote**

Si le remote est faux (par exemple l’utilisateur a été défini dans l’url de remote comme ci-dessous)

![](https://lh6.googleusercontent.com/viZA0J48XlzcSR_wHAicangr6Z05E6Dg_d26SQr46jni-XX3l-auQ83nhKoPXTMNKzhOVwC0O-jK1acB1FnQTgtpZPMJikiHzkANVWrf_qFu_pmsNf5nqdbONnX19pBT_Y9B9NI =605x55)

git remote set-url <name>

![](https://lh6.googleusercontent.com/_x76vG1btScuCap6JXa1qXewoGMAb2HWtpl1hkiBpq8N-BAje_PST-326dtnwT0jlLbF-V5rOIuT-yUHELvooMP6ij5pa6mVp-lCRwNjcz312CC1qiuUq2ad7_cH9MyysJpQpV4 =605x25)

Vérifier le changement

![](https://lh5.googleusercontent.com/pllYTXus5bFxYhvMkc2UxAwQ8BuhWpCjoNpLjCLAVeEdN9mTwwb6d_0pr4u6DvjPQcBU3SdgeRCcyK13dk4z8fL0QE78NT6nNpZyJ2BRhBCWfHpDuk8ihjgYc8KCKn7vRc3hgfg =593x60)

# **Changer de branche**

Effectuer un pull pour avoir la référence de la branche :

git pull

Effectuer le checkout pour changer de branche

git checkout <branch>

![](https://lh6.googleusercontent.com/HqkZe2CBmeUvHRopLs5mi5KekO2pDyWYLyTAJqq1_7T_i1SbksKdS2q7xgPzKldPIwh6D28w0uloqM9aTtsgRcbYkkLqpv9Vcr7VoNtkDcoQ-lWPkfI_KjTi_GliHybNKuR4paE =605x47)

![](https://lh4.googleusercontent.com/RsVra0EHks-At71rhv4x1iNxEuCjw0YyfhCbhq_m70SnKGbkfCbqilZLg5JLNz1x7K5ZjnEH1Gxsray49gJSSV5Ir7vs46wrPYlF18sx8N1Kel65WZ3j8XNV1J9eYSETzE7xlFY =414x61)

# **Résoudre des conflits**

Tout d’abord il est important de dire que les changements ne doivent pas être effectués directement sur un serveur de prod.

Si vraiment, les modifications doivent être commit depuis le serveur afin que les développeurs puissent au moins les récupérer en local.

Règle n°2, toujours faire un _pull_ lorsque l’on commence à travailler sur un projet afin d’être sur d’être à jour.

Si toutefois le repo git sur le serveur met ce genre d’erreur :

![](https://lh3.googleusercontent.com/t-8ain0duHlFs__19npVru2q2fW0thqvN-k9Abt-iTBEVkX5m_6LmKUSgL38fjlRx8J9iY-cNv38zPgcpthOXVoI9jsKWmrFQUKHlbTKy-V5ZoTnLcko5HmXxzCJ3gNus9artO8 =605x227)

On peut :

1. Considérer que la personne qui a modifié des données directement sur le serveur mérite qu’on regarde ce qu’elle a fait malgré les avertissements au début du présent chapitre.

Dans ce cas, la commande git diff permet de voir le travail effectué. L’idéal est de répercuter les modifications en local et créer un nouveau commit. Puis effectuer la même action qu’au point 2.

![](https://lh4.googleusercontent.com/GhGvR_FjSAJHBUjdoAsB7PZMEfu4z6Ga5RGIdBchX1pIdjjujO1tA1ypLg5g6F09vCwLnUc0Q4ypUU4Flq8GNKUMnmPPLNpBp52Wq1g4acnyxdnrfkAJF3QsHlwwFw2pGI4hr2k =393x305)

2. Considérer que la personne qui a modifié le code directement sur le serveur pourra recommencer.

Afin de récupérer le code présent sur git et uniquement celui là.

git reset –hard

Cette commande permet de revenir au dernier commit.

![](https://lh4.googleusercontent.com/VKDYDVGyi4hoYZPkdaY0EwzWk0vPUFSFpsekzEB0uWmK4wS7UBgWzWi4KIfr40eP0USVyY2rqtT3uiY6xujeMBUeMowRWc-fOFbzgwGVYWzBJNDjArqAKyFZF54sRgGv1JOvXqE =499x40)

Puis git pull permet de récupérer les dernières modifications du repo.

![](https://lh4.googleusercontent.com/fFjD63ci0j5W1V7w8JStabd2i5AJun3cgYB9WP-Pz60q1FTurUAuEs-Yd0HqXopLIdVoWe2i20OO_efS3B14BYejt8yZ2jptx4Y5gk3GH5kbsJDZrt6TtS4vSqwITJgqcCUHZ1Q =497x174)