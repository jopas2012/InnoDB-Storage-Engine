## Activitat 3. INNODB part II. REALITZA ELS SEGÜENTS APARTATS (obligatòria)  (1 punt)
•	Partint de l'esquema anterior configura el Percona Server perquè cada taula generi el seu propi tablespace en una carpeta anomenada tspaces (aquesta pot estar situada a on vulgueu).

   Per començar hem de assignar el innodb_file_per_table=ON
   
   ![image](https://user-images.githubusercontent.com/61474562/161385747-8dcf1221-40a6-477f-b7ee-69d0ab2a0765.png)


•	Indica quins són els canvis de configuració que has realitzat.
   
   Aturem el servei Mysql:
   
   ![image](https://user-images.githubusercontent.com/61474562/161385871-9da0cb45-469b-4c95-b0b2-fd0df730f26c.png)
   
   Creem el directori tablespaces:
   
      sudo mkdir /tspaces
      sudo chown -R mysql:mysql /tspaces
      sudo chmod 751 /tspaces
   
   Copiem el contingut del directori /var/lib/mysql al nou directori tablespaces:
   
      cp -R -p /var/lib/mysql/* /tspaces
   
   Hem de cambiar la ruta del datadir en el fitxer de configuració /etc/my.cnf:
    
    datadir=/tspaces
    
   ![image](https://user-images.githubusercontent.com/61474562/161386444-83b5990a-6ee8-4a83-a312-06fd5ed050a4.png)

    
   Iniciem el Servei MySQL:
    
    systemctl start mysql
    systemctl status mysql
      
  ![image](https://user-images.githubusercontent.com/61474562/161386459-54a1f7ea-af37-4a0e-b24d-d3ecfdbe5efb.png)

   Si comprovem el contingut del nou directori podem veure que els tablespace s'han creat
   
   ![image](https://user-images.githubusercontent.com/61474562/160896697-1fded80d-a29e-4ef0-96c1-b8fc97671bcd.png)

