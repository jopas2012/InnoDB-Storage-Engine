## Activitat 3. INNODB part II. REALITZA ELS SEGÜENTS APARTATS (obligatòria)  (1 punt)
•	Partint de l'esquema anterior configura el Percona Server perquè cada taula generi el seu propi tablespace en una carpeta anomenada tspaces (aquesta pot estar situada a on vulgueu).

•	Indica quins són els canvis de configuració que has realitzat.
   
   Hem de cambiar la ruta del datadir en el fitxer de configuració /etc/my.cnf:
    
    datadir='/var/lib/mysql/tablespaces'
    
   ![image](https://user-images.githubusercontent.com/61474562/160895893-240a32aa-e6ba-4531-965f-babb20b3ccf1.png)
   
   Una vegada modificat el fitcher /etc/my.cnf creem la carpeta on volem guardar els tablespace
   
   ![image](https://user-images.githubusercontent.com/61474562/160896344-7ed095cb-9678-4c7f-9b0f-f8b9d9b6bfd0.png)
    
   Reiniciem el Servei MySQL:
    
    systemctl restart mysql
   
   Si comprovem el contingut del nou directori podem veure que els tablespace s'han creat
   
   ![image](https://user-images.githubusercontent.com/61474562/160896697-1fded80d-a29e-4ef0-96c1-b8fc97671bcd.png)

