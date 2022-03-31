## Activitat 2. INNODB part I. REALITZA ELS SEGÜENTS APARTATS
1. Desactiva l’opció que ve per defecte de innodb_file_per_table
    Per desactivar l’opció innodb_file_per_table es pot fer per sessió o per sistema afegint la seguent línea al my.cnf
        
        innodb_file_per_table=0;
    En el meu cas l'he desactivat per sessió amb el seguent SET:
    
        SET GLOBAL innodb_file_per_table=0;
    
    ![image](https://user-images.githubusercontent.com/61474562/158662205-a1b28dd0-1984-42c0-9488-28afbfda478c.png)

2. Importa la BD Sakila com a taules InnoDB. 
    ![image](https://user-images.githubusercontent.com/61474562/158664448-a3c5b17c-017a-4dd4-bc51-0438546d39c4.png)


3.    Quin/quins són els fitxers de dades? A on es troben i quin és la seva mida?
   
   Al haber desactivat l'opció innodb_file_per_table el fitxer de dades ha cambiat i es troba en el ibdata1
    
   ![image](https://user-images.githubusercontent.com/61474562/158664069-7feedcc4-5e4c-4c5e-819b-36ac975e1222.png)
   
4.    Canvia la configuració del MySQL per:
      - Canviar la localització dels fitxers del tablespace de sistema per defecte a /discs-mysql/
      - Tinguem dos fitxers corresponents al tablespace de sistema.
      - Tots dos han de tenir la mateixa mida inicial (10MB) 
      - El tablespace ha de créixer de 5MB en 5MB.
      - Situa aquests fitxers (de manera relativa a la localització per defecte) en una nova localització simulant el següent:
      - /discs-mysql/disk1/primer fitxer de dades → simularà un disc dur
      - /discs-mysql/disk2/segon fitxer de dades → simularà un segon disc dur.
        
            innodb_file_per_table=1
            innodb_data_home_dir = /var/lib/mysql/discs-mysql
            innodb_data_file_path=/var/lib/mysql/discs-mysql/disk1/primer:10M;/var/lib/mysql/discs-mysql/disk2/segon:10M:autoextend


