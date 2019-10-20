---
# TP : TRAITEMENT DE DONNEES EN TABLES
---

Dans ce TP nous allons utiliser le travail effectués sur le notebook dédié aux manipulations de tables (y insérer le lien). 
Pour cela nous allons nous exercer sur des données importées depuis un fichier CSV contenant des relevés MétéoFrance, 
disponibles en ligne sur cette page. Plus précisément, nous allons nous intéresser aux relevés météo du mois de septembre 2019 (Télécharger).

## Import du fichier CSV
1) Charger la base de donnée sous la forme d'un dictionnaire ordonné dans la variable ` table_dict ` (le fichier csv utilise les 
points-virgules comme séparateurs)
2) Pour ce TP, nous n’avons pas besoin de conserver l’ensemble des champs de chaque enregistrement. Seuls les champs suivants nous intéressent :
- ` numer_sta `: l'identifiant de la station météo
- ` ff ` : la vitesse du vent moyen les dix dernières minutes, en m/s
- ` t ` : la température en Kelvin
- ` u ` : l'humidité en pourcentage
- ` rr1 ` : les précipitations dans la dernière heure, en mm

Récupérer uniquement ces champs en parcourant la structure `table_dict ` chargée précédemment puis 
en traduisant dans le type correct (flottant ou entier) les champs numériques (qui sont sinon tous traités comme des chaînes de caractères):
3) Modifier ce dictionnaire de sorte que :
 - la vitesse du vent soit en km/h (on appellera ` vitesse_vent ` le nouveau champ)
 - la température en degrés Celsius (on appellera ` temperature ` le nouveau champ)
 - les champ ` numer_sta `, ` u ` et ` rr1 ` soit renommés ` id ` , ` humidite ` et ` precipitations `
 
Attention, certains enregistrements sont incomplets, certains de leurs champs étant alors égaux à mq: 
on ne considèrera pas les enregistrements dont l’un des champs ` ff `, ` t `, ` u ` ou ` rr1 ` est égal à ` mq `. 

Vous devriez normalement récupérer 12 860 enregistrements complets.

## Statistiques
1. Écrire une fonction renvoyant la température minimale relevée.
2. Écrire une fonction renvoyant l’identifiant de la station météo ayant relevé la vitesse maximale de vent.
3. Écrire une fonction renvoyant le taux d’humidité moyen sur l’ensemble des relevés.
4. Écrire une fonction renvoyant le niveau de précipitation moyen relevés par les stations ayant un identifiant compris entre 60000 et 69999?

## Tris
5. Utilisons les fonctions de tri de la librairie standard de Python afin de trier la liste des enregistrements 
par numéro d’identification croissant.

## Fusion
Comparons les relevés de septembre 2019 avec ceux de septembre 2009. Un fichier similaire pour février 2009 est disponible (Télécharger).

Plus précisément, on cherche à comparer les relevés de température des stations en activité lors de ces deux mois
(les identifiants des stations météo n’ont pas changé depuis, mais certains stations ont disparu et d’autres sont apparues), 
pour chaque relevé. On va donc se servir également d’un champ supplémentaire des fichiers :

- ` date ` : la date du relevé sous le format ` AAAAMMJJhhmmss `

6) Écrire une fonction permettant de fusionner les deux tables extraites des fichiers de 2009 et de 2019, pour conserver 
dans chaque enregistrement l’identifiant de la station, la date du relevé de laquelle on supprime l’année, et deux champs ` t2009 ` et 
` t2019 ` donnant le relevé de température (différent de ` mq `) en février 2009 et février 2019, respectivement.
7) Utiliser la table fusionnée pour en déduire lequel des deux mois a été le plus chaud.
