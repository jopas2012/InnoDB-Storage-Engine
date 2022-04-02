## Activitat 3. INNODB part II. REALITZA ELS SEGÜENTS APARTATS (obligatòria)  (1 punt)
•	Partint de l'esquema anterior configura el Percona Server perquè cada taula generi el seu propi tablespace en una carpeta anomenada tspaces (aquesta pot estar situada a on vulgueu).

   Per començar hem de assignar el innodb_file_per_table=ON
   
   ![image](https://user-images.githubusercontent.com/61474562/161385747-8dcf1221-40a6-477f-b7ee-69d0ab2a0765.png)


•	Indica quins són els canvis de configuració que has realitzat.
   
   Aturem el servei Mysql:
   
   ![image](https://user-images.githubusercontent.com/61474562/161385871-9da0cb45-469b-4c95-b0b2-fd0df730f26c.png)
   
   Creem el directori tablespaces:
   
      sudo mkdir /tablespaces
      sudo chown -R mysql:mysql /tablespaces
      sudo chmod 751 /tablespaces
   
   Copiem el contingut del directori /var/lib/mysql al nou directori tablespaces:
   
      cp -R -p /var/lib/mysql/* /tablespaces
   
   Hem de cambiar la ruta del datadir en el fitxer de configuració /etc/my.cnf:
    
    datadir=/tablespaces
    
   ![image](https://user-images.githubusercontent.com/61474562/161386037-d409d809-2123-4e15-b2ba-3ad88d81779f.png)
    
   Iniciem el Servei MySQL:
    
    systemctl start mysql
    systemctl status mysql
   
   Si comprovem el contingut del nou directori podem veure que els tablespace s'han creat
   
   ![image](https://user-images.githubusercontent.com/61474562/160896697-1fded80d-a29e-4ef0-96c1-b8fc97671bcd.png)

