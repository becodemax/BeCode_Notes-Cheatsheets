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

```
create table 6digits (
    id int not null auto_increment,
    number int not null,
    primary key (id)
);

insert into 6digits
(id, number)
values ("1", "1");
```