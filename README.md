<p align="center">
<img src="./assets/img/screenshot.png" />
</p>

# sql-exercices
Ce repo contient les exercices SQL effectués lors de la formation POEC Java Sophia du 16/09 au 05/12/2024.  
L'ensemble des requêtes ont été exécutées sur le shell de XAMPP sous Windows.

# Connexion à phpmyadmin
La commande pour se connecter à phpmyadmin est la suivante :  
`mysql -h localhost -u root -p lpecom_db`

# Exercices

| Ex.1 | Quelle requête utiliser pour afficher l'ensemble des enregistrements de la table lpecom_livres ? |
| ------------- | ------------- |
| Réponse | `select * from lpecom_livres;` |
| - | <p align="center"><img src="./assets/img/exo1.png" /></p> |

| Ex.2 | Quelle requête utiliser pour sélectionner uniquement les livres qui ont un prix strictement supérieur à 20 dans la table lpecom_livres ? |
| ------------- | ------------- |
| Réponse | `select * from lpecom_livres where prix > 20;` |
| - | <p align="center"><img src="./assets/img/exo2.png" /></p> |

| Ex.3 | Quelle requête utiliser pour trier les enregistrements de la table lpecom_livres du prix le plus élevé au prix le plus bas ? |
| ------------- | ------------- |
| Réponse | `select * from lpecom_livres order by prix desc;` |
| - | <p align="center"><img src="./assets/img/exo3.png" /></p> |

| Ex.4 | Quelle requête utiliser pour récupérer le prix du livre le plus élevé de la table lpecom_livres ? |
| ------------- | ------------- |
| Réponse | `select * from lpecom_livres order by prix desc limit 1;` |
| - | <p align="center"><img src="./assets/img/exo4.png" /></p> |

| Ex.5 | Quelle requête utiliser pour récupérer les livres de la table lpecom_livres qui ont un prix compris entre 20 et 22 ? |
| ------------- | ------------- |
| Réponse | `select * from lpecom_livres where prix >= 20 and prix <= 22;` |
| - | <p align="center"><img src="./assets/img/exo5.png" /></p> |

| Ex.6 | Quelle requête utiliser pour récupérer tous les livres de la table lpecom_livres à l'exception de celui portant la valeur pour la colonne isbn_10 : 2092589547 ? |
| ------------- | ------------- |
| Réponse | `select * from lpecom_livres where isbn_10 != 2092589547;` |
| - | <p align="center"><img src="./assets/img/exo6.png" /></p> |

| Ex.7 | Quelle requête utiliser pour récupérer le prix du livre le moins élevé de la table lpecom_livres en renommant la colonne dans les résultats par minus ? |
| ------------- | ------------- |
| Réponse | `select prix as minus from lpecom_livres order by prix asc limit 1;` |
| - | <p align="center"><img src="./assets/img/exo7.png" /></p> |

| Ex.8 | Quelle requête utiliser pour sélectionner uniquement les 3 premiers résultats sans le tout premier de la table lpecom_livres ? |
| ------------- | ------------- |
| Réponse | `select * from lpecom_livres order by prix desc limit 3 offset 1;` |
| - | <p align="center"><img src="./assets/img/exo8.png" /></p> |

| Ex.9 | Quelle requête utiliser pour afficher l'id des étudiants qui ont participé à au moins un examen ? |
| ------------- | ------------- |
| Réponse | `select * from lpecom_etudiants as lpet, lpecom_examens as lpex where lpet.id_etudiant=lpex .id_etudiant;` |
| - | <p align="center"><img src="./assets/img/exo9.png" /></p> |

| Ex.10 | Quelle requête utiliser pour compter le nombre d'étudiants qui ont participé à au moins un examen ? |
| ------------- | ------------- |
| Réponse | `select count(distinct(lpecom_etudiants.id_etudiant)) as nbParticipantsExamen from lpecom_etudiants inner join lpecom_examens on lpecom_etudiants.id_etudiant=lpecom_examens.id_etudiant;` |
| - | <p align="center"><img src="./assets/img/exo10.png" /></p> |

| Ex.11 | Quelle requête utiliser pour calculer la moyenne de l'examen portant l'id : 45 ? |
| ------------- | ------------- |
| Réponse | `select avg(note) from lpecom_examens where id_examen=45;` |
| - | <p align="center"><img src="./assets/img/exo11.png" /></p> |

| Ex.12 | Quelle requête utiliser pour récupérer la meilleure note de l'examen portant l'id : 87 ? |
| ------------- | ------------- |
| Réponse | `select max(note) from lpecom_examens where id_examen=87;` |
| - | <p align="center"><img src="./assets/img/exo12.png" /></p> |

| Ex.13 | Quelle requête utiliser pour afficher l'id des étudiants qui ont eu plus de 11 à l'examen 45 ou plus de 12 à l'examen 87 ? |
| ------------- | ------------- |
| Réponse | `select id_etudiant from lpecom_examens where (id_examen=45 and note>11) or (id_examen=87 and note>12);` |
| - | <p align="center"><img src="./assets/img/exo13.png" /></p> |

| Ex.14 | Quelle requête utiliser pour afficher tous les enregistrements de la table lpecom_examens avec en plus, si c'est possible, le prénom et le nom de l'étudiant ? |
| ------------- | ------------- |
| Réponse | `select * from lpecom_examens inner join lpecom_etudiants on lpecom_examens.id_etudiant=lpecom_etudiants.id_etudiant;` |
| - | <p align="center"><img src="./assets/img/exo14.png" /></p> |

| Ex.15 | Quelle requête utiliser pour afficher les enregistrements de la table lpecom_examens avec le prénom et le nom de l'étudiant, uniquement quand les étudiants sont présents dans la table lpecom_etudiants ? |
| ------------- | ------------- |
| Réponse | `select * from lpecom_examens inner join lpecom_etudiants where lpecom_examens.id_etudiant=lpecom_etudiants.id_etudiant;` |
| - | <p align="center"><img src="./assets/img/exo15.png" /></p> |

| Ex.16 | Quelle requête utiliser pour afficher uniquement le nom et le prénom de l'étudiant avec l'id : 30 avec la moyenne de ses deux examens dans une colonne moyenne ? |
| ------------- | ------------- |
| Réponse | `select nom, prenom, avg(note) as moyenne from lpecom_examens inner join lpecom_etudiants where lpecom_examens.id_etudiant=30;` |
| - | <p align="center"><img src="./assets/img/exo16.png" /></p> |

| Ex.17 | Quelle requête utiliser pour afficher les 3 meilleurs examens, du meilleur au moins bon, avec le prénom et le nom de l'étudiant associé ? |
| ------------- | ------------- |
| Réponse | `select * from lpecom_examens inner join lpecom_etudiants where lpecom_examens.id_etudiant=lpecom_etudiants.id_etudiant order by note desc limit 3;` |
| - | <p align="center"><img src="./assets/img/exo17.png" /></p> |

| Ex.18 | Quel est le résultat de la requête ci-dessous ? |
| ------------- | ------------- |
| Réponse | `SELECT id, prenom, nom FROM lpecom_realisateurs WHERE nation = "us" AND sexe = 1;` |
| - | <p align="center"><img src="./assets/img/exo18.png" /></p> |

| Ex.19 | Quel est le résultat de la requête ci-dessous ? |
| ------------- | ------------- |
| Réponse | `SELECT * FROM lpecom_realisateurs WHERE sexe = "0" ORDER BY nom DESC LIMIT 1;` |
| - | <p align="center"><img src="./assets/img/exo19.png" /></p> |

| Ex.20 | Quel est le résultat de la requête ci-dessous ? |
| ------------- | ------------- |
| Réponse | `SELECT f.id, f.nom AS film, r.prenom, r.nom FROM lpecom_films f INNER JOIN lpecom_realisateurs r ON f.id_realisateur = r.id   ORDER BY f.id ASC;` |
| - | <p align="center"><img src="./assets/img/exo20.png" /></p> |

| Ex.21 | Quel est le résultat de la requête ci-dessous ? |
| ------------- | ------------- |
| Réponse | `SELECT f.id, f.nom AS film, r.prenom, r.nom FROM lpecom_films f LEFT JOIN lpecom_realisateurs r ON f.id_realisateur = r.id ORDER BY f.id ASC;` |
| - | <p align="center"><img src="./assets/img/exo21.png" /></p> |

| Ex.22 | Quel est le résultat de la requête ci-dessous ? |
| ------------- | ------------- |
| Réponse | `SELECT f.id, f.nom, fn.note FROM lpecom_films f LEFT JOIN lpecom_films_notes fn ON f.id = fn.id_film ORDER BY f.id ASC;` |
| - | <p align="center"><img src="./assets/img/exo22.png" /></p> |

| Ex.23 | Quel est le résultat de la requête ci-dessous ? |
| ------------- | ------------- |
| Réponse | `SELECT f.nom, r.prenom AS realisateur_prenom, r.nom AS realisateur_nom, AVG(fn.note) AS moyenne_note FROM lpecom_films f INNER JOIN lpecom_realisateurs r ON f.id_realisateur = r.id INNER JOIN lpecom_films_notes fn ON f.id = fn.id_film WHERE f.id = 546` |
| - | <p align="center"><img src="./assets/img/exo23.png" /></p> |

| Ex.24 | Quel est le résultat de la requête ci-dessous ? |
| ------------- | ------------- |
| Réponse | `SELECT r.nation, AVG(fn.note) AS moyenne_note FROM lpecom_films f INNER JOIN lpecom_realisateurs r ON f.id_realisateur = r.id INNER JOIN lpecom_films_notes fn ON f.id = fn.id_film WHERE r.nation = 'us';` |
| - | <p align="center"><img src="./assets/img/exo24.png" /></p> |

| Ex.25 | Quel est le résultat de la requête ci-dessous ? |
| ------------- | ------------- |
| Réponse | `SELECT r.nation, MAX(fn.note) AS max_note FROM lpecom_films f INNER JOIN lpecom_realisateurs r ON f.id_realisateur = r.id INNER JOIN lpecom_films_notes fn ON f.id = fn.id_film WHERE r.nation = 'uk';` |
| - | <p align="center"><img src="./assets/img/exo25.png" /></p> |

| Ex.26 | Quelle requête utiliser pour retrouver la ville qui possède les coordonnées GPS suivantes : 48.66913724637683, 1.87586057971015 ? |
| ------------- | ------------- |
| Réponse | `select name, gps_lat, gps_lng from lpecom_cities where gps_lat=48.66913724637683 and gps_lng=1.87586057971015;` |
| - | <p align="center"><img src="./assets/img/exo26.png" /></p> |

| Ex.27 | Sans jointure, quelle requête utiliser pour calculer le nombre de villes que compte le département de l'Essonne ? |
| ------------- | ------------- |
| Réponse | `select count(lc.name) as nbVilleEssone from lpecom_departments ld, lpecom_cities lc where ld.name=’Essonne’ and (lc.department_code=ld.code);` |
| - | <p align="center"><img src="./assets/img/exo27.png" /></p> |

| Ex.28 | Sans jointure, quelle requête utiliser pour calculer le nombre de villes en Île-de-France se terminant par '-le-Roi' ? |
| ------------- | ------------- |
| Réponse | `select count(*) from lpecom_cities lc, lpecom_departments ld, lpecom_regions lr where (lr.name='Île-de-France') and (lr.code=ld.region_code) and (ld.code=lc.department_code) and (lc.name like '%-le-Roi');` |
| - | <p align="center"><img src="./assets/img/exo28.png" /></p> |

| Ex.29 | Combien de villes possèdent le code postal (zip_code) 77320 ? Renommez la colonne de résultat n_cities. |
| ------------- | ------------- |
| Réponse | `select count(name) as n_cities from lpecom_cities where zip_code=77320;` |
| - | <p align="center"><img src="./assets/img/exo29.png" /></p> |

| Ex.30 | Sans jointure, quelle requête utiliser pour calculer le nombre de villes commençant par 'Saint-' en Seine-et-Marne ? |
| ------------- | ------------- |
| Réponse | `select count(*) from lpecom_cities lc, lpecom_departments ld where (lc.name like 'Saint-%' and ld.name='Seine-et-Marne') and (lc.department_code=ld.code);` |
| - | <p align="center"><img src="./assets/img/exo30.png" /></p> |

| Ex.31 | Quelles villes possèdent un code postal (zip_code) compris entre 77210 et 77810 ? |
| ------------- | ------------- |
| Réponse | `select name, zip_code from lpecom_cities  where zip_code>=77210 and zip_code<=77810;` |
| - | <p align="center"><img src="./assets/img/exo31.png" /></p> |

| Ex.32 | Sans jointure, quelles sont les deux villes de Seine-et-Marne à avoir le code postal (zip_code) le plus grand ? |
| ------------- | ------------- |
| Réponse | `select lc.name, zip_code from lpecom_cities lc, lpecom_departments ld where (ld.name='Seine-et-Marne') and (lc.department_code=ld.code) order by zip_code desc limit 2;` |
| - | <p align="center"><img src="./assets/img/exo32.png" /></p> |

| Ex.33 | Quel est le code postal (zip_code) le plus grand de la table lpecom_cities ? |
| ------------- | ------------- |
| Réponse | `select name, zip_code from lpecom_cities lc order by zip_code desc limit 1;` |
| - | <p align="center"><img src="./assets/img/exo33.png" /></p> |

| Ex.34 | Avec un seul WHERE et aucun OR, quelle est la requête permettant d'afficher les départements des régions ayant le code suivant : 75, 27, 53, 84 et 93 ? Le résultat doit afficher le nom du département ainsi que le nom et le slug de la région associée. |
| ------------- | ------------- |
| Réponse | `select ld.name, lr.name, lr.slug from lpecom_departments ld, lpecom_regions lr where ld.region_code=lr.code and ld.region_code in (‘75’, ‘27’, ‘53’, ‘84’, ‘93’);` |
| - | <p align="center"><img src="./assets/img/exo34.png" /></p> |

| Ex.35 | Point important, il sera sans doute nécessaire d'utiliser AS pour obtenir le résultat souhaité. Quelle requête utiliser pour obtenir en résultat, les noms de la région, du département et de chaque ville du département ayant pour code 77 ? |
| ------------- | ------------- |
| Réponse | `select lr.name, ld.name, lc.name from lpecom_departments ld, lpecom_regions lr, lpecom_cities lc where (lc.department_code=ld.code) and (ld.region_code=lr.code) and ld.code=‘77’;` |
| - | <p align="center"><img src="./assets/img/exo35.png" /></p> |

| Ex.36 | Quelle requête utiliser pour afficher toutes les données de vaccination uniquement pour le 1er avril 2021 ? |
| ------------- | ------------- |
| Réponse | `select * from lpecom_covid lc where lc.jour=’2021-04-01’;` |
| - | <p align="center"><img src="./assets/img/exo36.png" /></p> |

| Ex.37 | Quelle requête utiliser pour afficher toutes les données de vaccination uniquement pour le 1er avril 2021 avec le nom de la région concernée ? |
| ------------- | ------------- |
| Réponse | `select * from lpecom_covid lc, lpecom_regions lr where lr.code=lc.id_region and lc.jour=’2021-04-01’;` |
| - | <p align="center"><img src="./assets/img/exo37.png" /></p> |

| Ex.38 | Quelle requête utiliser pour afficher le nombre au cumulé de vaccination première dose toutes régions en 2020 ? Proposez également une solution pour les vaccination deuxième dose. |
| ------------- | ------------- |
| Réponse | `select sum(lc.n_dose1), sum(lc.n_dose2) from lpecom_covid lc where lc.jour >= ‘2020-01-01’ and lc.jour <= ‘2020-12-31’;` |
| - | <p align="center"><img src="./assets/img/exo38.png" /></p> |

| Ex.39 | Quelle requête SQL utiliser pour afficher le nombre au cumulé de vaccination première dose pour la région avec le code 93 uniquement pour le mois de mars 2021 ? |
| ------------- | ------------- |
| Réponse | `select sum(lc.n_dose1) from lpecom_covid lc where lc.id_region=93 and lc.jour >= ‘2021-03-01’ and lc.jour <= ‘2021-03-31’;` |
| - | <p align="center"><img src="./assets/img/exo39.png" /></p> |

| Ex.40 | Quelle requête utiliser pour afficher le nombre au cumulé de vaccination deuxième dose pour la région avec le code 11 uniquement pour le mois de mars 2021 ? ? |
| ------------- | ------------- |
| Réponse | `select sum(lc.n_dose2) from lpecom_covid lc where lc.id_region=11 and lc.jour >= ‘2021-03-01’ and lc.jour <= ‘2021-03-31’;` |
| - | <p align="center"><img src="./assets/img/exo40.png" /></p> |

| Ex.41 | Quelle requête SQL utiliser pour afficher le record de vaccination première dose en une seule journée ? Avec une deuxième requête, afficher les informations de la région concernée, dont son nom, ainsi que le jour du record. |
| ------------- | ------------- |
| Réponse | `select max(lc.n_cum_dose1), lr.name, lc.jour from lpecom_covid lc, lpecom_regions lr where lc.id_region=lr.code;` |
| - | <p align="center"><img src="./assets/img/exo41.png" /></p> |

| Ex.42 | Quelle requête utiliser pour afficher le record de vaccination deuxième dose en une seule journée ? Avec une deuxième requête, afficher les informations de la région concernée, dont son nom, ainsi que le jour du record. |
| ------------- | ------------- |
| Réponse | `seselect max(lc.n_cum_dose2), lr.name, lc.jour from lpecom_covid lc, lpecom_regions lr where lc.id_region=lr.code;` |
| - | <p align="center"><img src="./assets/img/exo42.png" /></p> |

| Ex.43 | Quelles requêtes permettent de connaitre quelle région possède la plus grande couverture de vaccination avec une dose et deux doses ?  
Vous aurez besoin de 4 requêtes pour répondre aux deux questions.  
Vous aurez besoin du résultat de la première requête pour la deuxième. |
| ------------- | ------------- |
| Réponse | `select max(lc.couv_dose1), lr.name from lpecom_covid lc, lpecom_regions lr where lc.id_region=lr.code;` |
| - | <p align="center"><img src="./assets/img/exo43.png" /></p> |

| Ex.44 | Quelle requête utiliser pour afficher le nom de la région qui a le plus faible taux de couverture de vaccination avec une dose ? Vous aurez besoin de 2 requêtes pour répondre à la question. |
| ------------- | ------------- |
| Réponse | `select min(lc.couv_dose1), lr.name from lpecom_covid lc, lpecom_regions lr where lc.id_region=lr.code;` |
| - | <p align="center"><img src="./assets/img/exo44.png" /></p> |

| Ex.45 | Quelle requête utiliser pour calculer la couverture moyenne entre les différentes régions à la date la plus récente, pour les vaccinations une et deux doses ? Vous renommez les colonnes de résultats : couverture_dose1_avg et couverture_dose2_avg. |
| ------------- | ------------- |
| Réponse | `select avg(lc.couv_dose1) as couverture_dose1_avg, avg(lc.couv_dose2) as couverture_dose2_avg from lpecom_covid lc, lpecom_regions lr where lc.id_region=lr.code order by lc.jour desc;` |
| - | <p align="center"><img src="./assets/img/exo45.png" /></p> |

| Ex.46 | Quelle requête utiliser pour afficher les données de vaccination des régions (avec leur nom) qui possèdent une couveture vaccinale supérieure à 15 % pour la première dose et supérieure à 5 % pour la deuxième dose ? |
| ------------- | ------------- |
| Réponse | `select * from lpecom_covid lc, lpecom_regions lr where lc.id_region=lr.code and  lc.couv_dose1 > 15;` |
| Réponse | `select * from lpecom_covid lc, lpecom_regions lr where lc.id_region=lr.code and  lc.couv_dose2 > 5;` |
| - | <p align="center"><img src="./assets/img/exo46.png" /></p> |
| - | <p align="center"><img src="./assets/img/exo46b.png" /></p> |

| Ex.47 | Sans jointure, quelle requête SQL utiliser pour afficher toutes les données de vaccination du 14 février 2021 uniquement, pour le département de Seine-et-Marne (77) ? |
| ------------- | ------------- |
| Réponse | `select * from lpecom_covid lcd, lpecom_departments ld where ld.name='Seine-et-Marne' and lcd.jour='2021-02-14';` |
| - | <p align="center"><img src="./assets/img/exo47.png" /></p> |

| Ex.48 | Sans jointure, quelle requête SQL utiliser pour afficher le cumul de toutes les données de vaccination pour tous les vaccins du 14 février 2021 uniquement, pour les départements de l'Essonne (91) et de la Seine-et-Marne (77) ? |
| ------------- | ------------- |
| Réponse | `select * from lpecom_covid lcd, lpecom_departments ld where (ld.name='Seine-et-Marne' or ld.name='Essonne') and lcd.jour='2021-02-14';` |
| - | <p align="center"><img src="./assets/img/exo48.png" /></p> |

| Ex.49 | Sans jointure, quelle requête utiliser pour afficher la somme des vaccinations première dose réalisées uniquement avec le vaccin AstraZeneka pour le mois de février 2021 pour le département de la Seine-et-Marne (77) ? |
| ------------- | ------------- |
| Réponse | `SELECT SUM(v.n_dose1) FROM lpecom_covid_vaccin v WHERE v.dep_code = 77 AND v.jour BETWEEN '2021-02-01' AND '2021-02-31' AND v.vaccin = 3;` |
| - | <p align="center"><img src="./assets/img/exo49.png" /></p> |

| Ex.50 | Sans jointure, quelle requête utiliser pour afficher la somme des vaccinations deuxième dose réalisées avec le vaccin AstraZeneka ou Moderna pour le mois de mars 2021 pour le département de la Seine-et-Marne (77) ? |
| ------------- | ------------- |
| Réponse | `select sum(v.n_dose2) from lpecom_covid_vaccin v where v.dep_code = 77 and (v.jour between '2021-03-01' and '2021-03-31') and (v.vaccin = 3 or v.vaccin = 2);` |
| - | <p align="center"><img src="./assets/img/exo50.png" /></p> |