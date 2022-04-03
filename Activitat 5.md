# Activitat 5. REDOLOG. REALITZA ELS SEGÜENTS APARTATS. (2 punt)

•	Com podem comprovar (Innodb Log Checkpointing)

•	LSN (Log Sequence Number)

•	L'últim LSN actualitzat a disc

•	Quin és l'últim LSN que se li ha fet Checkpoint

   Per comprovar-ho hem de fer servir la seguent comanda:
   
    SHOW ENGINE INNODB STATUS\G
    
   ![image](https://user-images.githubusercontent.com/61474562/161429343-f3d27800-300c-49ca-99e8-5fd0cf9d34bd.png)

•	Proposa un exemple a on es vegi l'ús del redolog
   
   El que vaig a fer és ampliar la mida dels fitxers REDLOG:
   
   Parar servei Mysql:
    
    systemctl stop mysql
    
   Esborrem els logs:
   
   ![image](https://user-images.githubusercontent.com/61474562/161435320-03215045-c084-4041-9c09-6fe7c8c191e7.png)

   Modifiquem la mida dels log_file en el fitxer de configuració /etc/my.cnf:
   
   ![image](https://user-images.githubusercontent.com/61474562/161435483-4f5c3a79-b4cc-471b-981b-f5c4fd3364e7.png)
   
   iniciem el servei Mysql:
   
   ![image](https://user-images.githubusercontent.com/61474562/161435185-f9713c61-ef27-4e77-8ca9-b1d24b92997a.png)

•  Com podem mirar el número de pàgines modificades (dirty pages)? I el número total de pàgines?

   Ho podem comprovar amb la seguent comanda:
   
      SHOW ENGINE INNODB STATUS\G
   
   Com no hem modificat cap pagina ens surten 0 pagines modificades:
   
   ![image](https://user-images.githubusercontent.com/61474562/161435956-ffee6e37-0f07-4e13-b04f-081b28def430.png)
