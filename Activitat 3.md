## Activitat 3. INNODB part II. REALITZA ELS SEGÜENTS APARTATS (obligatòria)  (1 punt)
•	Partint de l'esquema anterior configura el Percona Server perquè cada taula generi el seu propi tablespace en una carpeta anomenada tspaces (aquesta pot estar situada a on vulgueu).
    Hem de afegir la seguent característica a les taules del esquema:
    
    DATA DIRECTORY='/var/lib/mysql/tablespace_sakila'
    
   ![image](https://user-images.githubusercontent.com/61474562/160892814-3e7310da-f1ba-4448-add6-3e159050caaf.png)


•	Indica quins són els canvis de configuració que has realitzat.
