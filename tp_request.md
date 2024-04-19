# Travaux pratiques MongoDB
author: MBOCK MBOCK Georges christiian

date: 19/04/2024


## Objectifs: 
* 1- Construire une base de données 

* 2- Manipulation des données

### 1- Construire la base de données

Dans cette partie, nous allons énumérer les étapes faites:

* création d'une instance sur le port 27019 avec la commande `mongod --port 27019 --dbpath path_of_folder_name`

* création de la base de données par importation des données grâce à la commande `mongoimport --db firstTp --collection firstCollection --file dblp.json --host localhost --port
27019 --jsonArray --type json`  où firstTp est le nom de notre base de données et firstCollection est le nom de notre collection

* après nous sommes connectés à notre instance avec la commande `mongosh --port 27019 firstTp`


### 2- Manipulation des données

#### TP-1

1- afficher le premier document `db.fiirstCollection.find().limit(1)`

2- affichher tous les documents `db.firstCollection.find()`

3-Liste de tous les livres de type « Book » : `db.firstCollection.find({type: 'Book'})`

4- Liste des publications depuis 2011: `db.firstCollection.find({year: {$gt: 2010}})`

5- Liste des livres depuis 2014 : `db.firstCollection.find({year: {$gt: 2013}})`

6- Liste des publications de l’auteur « Toru Ishida » : `db.firstCollection.find({authors: 'Toru Ishida'})`

#### TP-2

1- Liste de tous les auteurs distincts : `db.firstCollection.distinct("authors")`

2- Trier les publications de « Toru Ishida » par titre de livre et par page de début : `db.firstCollection.find({authors: 'Toru Ishida'}).sort({booktitle: 1, pages: 1})`

3- Projeter le résultat sur le titre de la publication et les pages : `db.firstCollection.find({}, {_id : 0, type: 0, year: 0, booktitle: 0, url: 0, authors: 0, publisher:0, series:0, isbn:0})`

4- Compter le nombre de publications de la collection : `db.firstCollection.find().count("publisher")`

5- Compter le nombre de publications entre 1986 et 2015 : `db.firstCollection.find({year: {$gt : 1985, $lte: 2015}}).count("publisher")`
