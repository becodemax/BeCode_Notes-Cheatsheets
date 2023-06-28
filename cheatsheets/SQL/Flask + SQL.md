```
create table if not exists formulaire (
	nom text,
	prenom text,
	email text,
	pays text,
	genre text,
	demande text,
	message text
);

create table if not exists creds (
	username text,
	password text
);
```

```
insert into formulaire
(nom, prenom, email, pays, genre, demande, message)
values ("Einstein", "Albert", "e.albert@gmail.com", "Allemagne", "M", "Demande", "Ich bin ein Berliner.");

insert into creds
(username, password)
values ("test", "test");
```