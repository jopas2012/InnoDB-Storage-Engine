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
   
   Parar servei Mysql
    
    systemctl stop mysql
    
   
