## Activitat 4. INNODB part III. REALITZA ELS SEGÜENTS APARTATS (obligatòria)  (1 punt)

•	Crea un tablespace anomenat 'ts1' situat a /discs-mysql/disc1/ i col·loca les taules actor, address i category de la BD Sakila.

  Per crear el tablespace només a les taules actor, adress i category hem de crear una taula ts1 amb el DATA FILE que tindrà la ruta /discs-mysql/disc1/, seguidament hem de modificar les 3 taules de la bd Sakila i afegir com a TABLESPACE la taula que hem creat abans amb el nom de ts1:
  
    CREATE TABLESPACE ts1 ADD DATAFILE '/discs-mysql/disc1/ts1.ibd' ENGINE=InnoDB;
    USE sakila;
    ALTER TABLE actor TABLESPACE ts1;
    ALTER TABLE address TABLESPACE ts1;
    ALTER TABLE category TABLESPACE ts1;
    
