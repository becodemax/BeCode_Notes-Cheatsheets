- Affiche toutes les données.
```
select * from students, school;
```
- Affiche uniquement les prénoms.
```
select prenom from students;
```
- Affiche les prénoms, les dates de naissance et l’école de chacun.
```
select prenom, datenaissance, school from students;
```
- Affiche uniquement les élèves qui sont de sexe féminin.
```
select nom, prenom from students where genre = "F";
```
- Affiche uniquement les élèves qui font partie de l’école d'Addy.
```
select nom, prenom from students where school = 1;
```
- Affiche uniquement les prénoms des étudiants, par ordre inverse à l’alphabet (DESC). Ensuite, la même chose mais en limitant les résultats à 2.
```
select prenom from students order by prenom desc;

select prenom from students order by prenom desc limit 2;
```
- Ajoute Ginette Dalor, née le 01/01/1930 et affecte-la à Bruxelles, toujours en SQL.
```
insert into students
(nom, prenom, datenaissance, genre, school)
values ("Dalor", "Ginette", "1930-01-01", "F", 1);
```
- Modifie Ginette (toujours en SQL) et change son sexe et son prénom en “Omer”.
```
update students
set genre = "M", prenom = "Omer"
	where nom = "Dalor";
```
- Supprimer la personne dont l’ID est 3.
```
delete from students
where idstudent = 3;
```
- Modifier le contenu de la colonne Schoselectol de sorte que "1" soit remplacé par "Liege" et "2" soit remplacé par "Gent". (attention au type de la colonne !)
```
update school
set school = "Liege"
	where idschool = 1;

update school
set school = "Gent"
	where idschool = 2;
```
- Faire d’autres manipulations pour voir si t’es bien compris.
```
             _     _ _   
  __ _  ___ | |_  (_) |_ 
 / _` |/ _ \| __| | | __|
| (_| | (_) | |_  | | |_ 
 \__, |\___/ \__| |_|\__|
 |___/
```