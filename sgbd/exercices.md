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

## 4 