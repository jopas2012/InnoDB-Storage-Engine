# Activitat 7. Storage Engine CSV (0,5  punts)

• Documenta i posa exemple de com utilitzar ENGINE CSV.

  El Engine CSV  emmagatzema dades en fitxers de text utilitzant el format de valors separats per comes.

  Quan creeu una CSV taula, el servidor crea un fitxer de dades de text sense format amb un nom que comença amb el nom de la taula i té una .CSVextensió. Quan emmagatzemeu dades a la taula, el motor d'emmagatzematge les desa al fitxer de dades en format de valors separats per comes.
  
  Amb la comanda podem comprobar que aquest motor ja el tenim instal·lat per defecte:
  
    SHOW ENGINES;
   
  ![image](https://user-images.githubusercontent.com/61474562/161436322-6947305c-92f3-4152-be00-f1791e1e3140.png)

  
• Cal documentar els passos que has hagut de realitzar per preparar l'exemple: configuracions, instruccions DML, DDL, etc....

   Creació d'una Base de Dades:
  
    CREATE DATABASE CSV;
   
   ![image](https://user-images.githubusercontent.com/61474562/161436442-b81f5aac-5b43-4ef0-8890-4f868c52be58.png)

   Creació Taula prova en la base de dades CSV:
   Per aquest motor CSV els camps de les taules no poden ser nuls.
   
    USE CSV;
    CREATE TABLE prova (a INT NOT NULL, b CHAR(10) NOT NULL) ENGINE = CSV;
    
  ![image](https://user-images.githubusercontent.com/61474562/161436601-ea427fee-539a-48d5-8442-015c2253d975.png)
   
  Insert a la taula Prova de la base de dades CSV:
    
    USE CSV;
    INSERT INTO prova VALUES(1,'dada_uno'),(2,'dada_dos');
    
   ![image](https://user-images.githubusercontent.com/61474562/161436724-bc915442-aa42-4c92-b1bc-d39b563013f6.png)

   
   Comprovació dels fitxers creats en la base de dades CSV:
   
   ![image](https://user-images.githubusercontent.com/61474562/161436917-b35d19e2-b701-4341-a1cf-9078aa2bfbb6.png)
    
