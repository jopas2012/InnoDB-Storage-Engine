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
    
    
