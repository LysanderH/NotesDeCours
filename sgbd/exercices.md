# SGBD Exercices

## 1 Select Simple

1. SELECT * FROM `ecole_eleves`;
1. SELECT DISTINCT * FROM `ecole_eleves`;
1. SELECT * FROM `ecole_resultats`;
1. SELECT * FROM `ecole_cours`;

## 2 Projections

1. SELECT nom, prenom FROM `ecole_eleves`;
1. SELECT DISTINCT nom, prenom FROM `ecole_eleves`;
1. SELECT nom, salaire_base, salaire_actuel FROM `ecole_professeurs`;
1. SELECT DISTINCT nom FROM `ecole_cours`;

## 3 Sélection avec critères simple
1. SELECT * FROM `ecole_eleves` WHERE annee=1;
1. 	SELECT * FROM `ecole_eleves` WHERE annee>1;  
	SELECT * FROM `ecole_eleves` WHERE annee<>1; plus lent  
	SELECT * FROM `ecole_eleves` WHERE annee!=1; fonctionne pas  
	SELECT * FROM `ecole_eleves` WHERE NOT annee=1;
1.  SELECT * FROM `ecole_eleves` WHERE nom='Brisefer';  
	SELECT * FROM `ecole_eleves` WHERE nom='brisefer';  
	la casse n'est pas pris en compte si ce n'est pas précisé
1.	SELECT * FROM `ecole_eleves` WHERE poids>45;
1.	SELECT * FROM `ecole_eleves` WHERE poids BETWEEN 45 AND 63;
1.	SELECT * FROM `ecole_activites` WHERE equipe LIKE 'AMC%';
1.	SELECT * FROM `ecole_activites` WHERE equipe LIKE '%i_';
1.	SELECT * FROM `ecole_professeurs` WHERE nom LIKE '%e';
1.	SELECT * FROM `ecole_activites` WHERE equipe LIKE '% %';
1.	SELECT * FROM `ecole_professeurs` WHERE specialite='poesie' OR specialite='sql';  
	SELECT * FROM `ecole_professeurs` WHERE specialite IN ('sql','poesie');  
	plus performant et plus court
1.	SELECT * FROM `ecole_eleves` WHERE poids=35 OR 42 OR 72 OR 78 OR 120;  
	SELECT * FROM `ecole_eleves` WHERE poids IN (35, 42, 72, 78, 120);
1.	SELECT specialite FROM `ecole_professeurs` WHERE specialite IS NOT NULL;
1.	SELECT nom FROM `ecole_professeurs` WHERE der_prom IS NULL;

## 4 Sélection avec critères multiples

1.	SELECT * FROM ecole_eleves WHERE poids>52 AND annee=1;
1.	SELECT * FROM ecole_professeurs WHERE salaire_base =1900000 AND specialite='recent';
1.	SELECT * FROM ecole_cours WHERE annee = 1 AND nbheurres = 15;

## 5 Fonctions de calcul

1.	SELECT AVG(poids) FROM ecole_eleves;
1.	SELECT AVG(poids) FROM ecole_eleves WHERE annee=1;
1.	SELECT MAX(poids) FROM ecole_eleves WHERE annee=2;
1.	SELECT COUNT(\*) FROM ecole_eleves WHERE annee=1;
1.	SELECT COUNT(\*) FROM ecole_eleves;
1.	SELECT SUM(salaire_base) FROM ecole_professeurs;
1.	SELECT MIN(salaire_base) FROM ecole_professeurs;
1.	SELECT MAX(poids) FROM ecole_eleves WHERE annee=3;
1.	SELECT COUNT(specialite) FROM ecole_professeurs;
1.	SELECT COUNT(DISTINCT specialite) FROM ecole_professeurs;
1.	SELECT COUNT(\*) FROM ecole_professeurs;
1.	SELECT COUNT(specialite) FROM ecole_professeurs WHERE specialite='sql';
1.	SELECT SUM(poids) FROM ecole_eleves WHERE annee=2;

## 6 Opérations arithmétique

1.	SELECT nom, salaire_actuel/12 FROM ecole_professeurs;
1.	SELECT nom, (salaire_actuel-salaire_base) FROM ecole_professeurs;
1.	SELECT nom, ((salaire_actuel-salaire_base) / 12) FROM ecole_professeurs;
1.	SELECT nom, (salaire_actuel-salaire_base) FROM ecole_professeurs WHERE (salaire_actuel-salaire_base) /12 > 0.28;
1.	SELECT AVG((salaire_actuel-salaire_base) / 12) FROM ecole_professeurs;

## 7 Opérations sur les dates

1.	SELECT CURRENT_DATE;
1.	SELECT nom FROM ecloe_eleves WHERE date_naissance < "1977-02-27";
1.	SELECT nom FROM ecole_professeurs WHERE date_naissance < "1988-10-11";

## Chapitre 8

1.	SELECT nom, prenom FROM ecole_eleves WHERE poids > (SELECT poids FROM ecole_eleves WHERE nom = "Brisefer");
1.	SELECT MIN(points) FROM ecole_resultats WHERE num_eleve = (SELECT nom FROM ecole_eleves WHERE nom ="Brisefer");

## Chapitre 9

1.	SELECT * FROM ecole_eleves JOIN ecole_activites_pratiquees USING (num_eleve) WHERE niveau = 1 AND ecole_activites_pratiquees.nom = "surf";
1.	SELECT ecole_eleves.nom FROM ecole_eleves JOIN ecole_activites_pratiquees USING (num_eleve) JOIN ecole_activites USING (niveau) WHERE equipe ="AMC indus";
1.	SELECT nom, points FROM ecole_resultats JOIN ecole_eleves USING (num_eleve) WHERE ecole_eleves.nom ="Tsuno";
1.	SELECT nom, points * 5 FROM ecole_resultats JOIN ecole_eleves USING (num_eleve) WHERE ecole_eleves.nom ="Tsuno";
1.  SELECT MIN(points) FROM ecole_resultats JOIN ecole_eleves USING (num_eleve) WHERE ecole_eleves.nom ="Brisefer"
1.	SELECT MIN(points), ecole_cours.nom FROM ecole_eleves JOIN ecole_resultats USING (num_eleve) JOIN ecole_cours USING (num_cours) WHERE ecole_eleves.nom ="Brisefer";

## Chapitre 10

1.	SELECT * FROM ecole_eleves ORDER BY nom ASC, prenom DESC;
1.	SELECT * FROM ecole_professeurs ORDER BY salaire_actuel DESC;
1.	SELECT nom, (points * 5) FROM  ecole_resultats JOIN ecole_eleves USING (num_eleve) WHERE ecole_eleves.nom ="Tsuno" ORDER BY points DESC;
exemples renomme la colonne et calcule la moyenne des salaire des profs	SELECT AVG(salaire_actuel) AS salaire_moyen, specialite FROM `ecole_professeurs` GROUP BY specialite;

## Chapitre 11

1.	SELECT nom, AVG(ecole_resultats.points) AS moyenne FROM 'ecole_eleves' JOIN 'ecole_resultats' USING(num_eleve) GROUP BY num_eleve;
exercice 
1.	SELECT nom, SUM(points) AS total FROM 'ecole_eleves' JOIN ecole_resultats USING(num_eleve) GROUP BY num_eleve;

## Chapitre 12

