## Activitat 4. INNODB part III. REALITZA ELS SEGÜENTS APARTATS (obligatòria)  (1 punt)

•	Crea un tablespace anomenat 'ts1' situat a /discs-mysql/disc1/ i col·loca les taules actor, address i category de la BD Sakila.

  Per crear el tablespace només a les taules actor, adress i category hem de crear una taula ts1 amb el DATA FILE que tindrà la ruta /discs-mysql/disck/, seguidament hem de modificar les 3 taules de la bd Sakila i afegir com a TABLESPACE la taula que hem creat abans amb el nom de ts1:
  
    CREATE TABLESPACE ts1 ADD DATAFILE '/discs-mysql/disk1/ts1.ibd' ENGINE=InnoDB;
    USE sakila;
    ALTER TABLE actor TABLESPACE ts1;
    ALTER TABLE address TABLESPACE ts1;
    ALTER TABLE category TABLESPACE ts1;
  
  ![image](https://user-images.githubusercontent.com/61474562/161386888-d929660c-d010-4e26-96b3-3cb5e67290a3.png)


•	Crea un altre tablespace anomenat 'ts2' situat a /discs-mysql/disc2/ i col·loca-hi la resta de taules.

  Hem de fer el mateix que anteriorment pero amb un fitxer ts2 i les taules que ens demana:
  
    CREATE TABLESPACE ts2 ADD DATAFILE '/discs-mysql/disk2/ts2.ibd' ENGINE=InnoDB;
    USE sakila;
    ALTER TABLE city TABLESPACE ts2;
    ALTER TABLE country TABLESPACE ts2;
    ALTER TABLE customer TABLESPACE ts2;
    ALTER TABLE language TABLESPACE ts2;
    ALTER TABLE payment TABLESPACE ts2;
    ALTER TABLE rental TABLESPACE ts2;
    ALTER TABLE staff TABLESPACE ts2;
    ALTER TABLE store TABLESPACE ts2;
    ALTER TABLE film TABLESPACE ts2;
    ALTER TABLE film_actor TABLESPACE ts2;
    ALTER TABLE film_category TABLESPACE ts2;
    ALTER TABLE film_text TABLESPACE ts2;
    ALTER TABLE inventory TABLESPACE ts2;
    
  ![image](https://user-images.githubusercontent.com/61474562/161387095-d576e843-c019-4562-b7b9-a3222c556207.png)

  Comprovem que s'han creat els fitxers .ibd:
  
  ![image](https://user-images.githubusercontent.com/61474562/161387148-5ed8777d-a5c3-4d01-aa0f-0a6f1ecead29.png)

•	Comprova que pots realitzar operacions DML a les taules dels dos tablespaces.

  Per comprovar-ho farem un insert a la taula actor i un altre a la taula city una de cada TABLESPACE:
  
  ![image](https://user-images.githubusercontent.com/61474562/161387256-83ab3078-1d05-4439-8b24-5c8d59353b8b.png)
  
  ![image](https://user-images.githubusercontent.com/61474562/161387274-062cfbf6-36f7-4c47-9798-75592985301e.png)

  Insert taula Actor:
  
    INSERT INTO actor(actor_id,first_name,last_name) VALUE(1,'Paco','Tabaco');

  ![image](https://user-images.githubusercontent.com/61474562/161387351-987cbb2e-1ae5-469d-93b4-01fd162fce66.png)

  ![image](https://user-images.githubusercontent.com/61474562/161387370-e3fb80f4-a2eb-4755-b0f7-a7095d6183cb.png)
  
  Insert taula City:
  
    INSERT INTO city(city_id,city,country_id) VALUE(1,'Madrid','1');

  ![image](https://user-images.githubusercontent.com/61474562/161387480-c45e4d06-a745-45a9-bfb4-a5385baeba0a.png)

  ![image](https://user-images.githubusercontent.com/61474562/161387486-8688692f-22db-4ab2-a5dc-f967c2280c25.png)
