## Activitat 2. INNODB part I. REALITZA ELS SEGÜENTS APARTATS
1. Desactiva l’opció que ve per defecte de innodb_file_per_table
    Per desactivar l’opció innodb_file_per_table es pot fer per sessió o per sistema afegint la seguent línea al my.cnf
        
        innodb_file_per_table=0;
    En el meu cas l'he desactivat per fitxer de configuració:
    
    ![image](https://user-images.githubusercontent.com/61474562/161381390-c0b58909-d299-41db-acd5-3185369f5ab8.png)
    
    Reiniciem el servei mysql
    
        systemctl restart mysql
        
    Comprovació:
    
    ![image](https://user-images.githubusercontent.com/61474562/161381496-87184314-a7de-45e8-903e-25d6918d1ed2.png)


2. Importa la BD Sakila com a taules InnoDB. 
    
    Importem l'esquema per defecte ja que ve amb les taules innodb:
    
    ![image](https://user-images.githubusercontent.com/61474562/158664448-a3c5b17c-017a-4dd4-bc51-0438546d39c4.png)


3.    Quin/quins són els fitxers de dades? A on es troben i quin és la seva mida?
   
   Aquests fitxers es troben al directori /var/lib/mysql/sakila
    
   ![image](https://user-images.githubusercontent.com/61474562/161381582-291f091a-20f0-4483-b179-fdbd5efbdc73.png)
   
   Quan innodb_file_per_table=OFF, InnoDB emmagatzema totes les taules a l'espai de taula del sistema InnoDB, en aquest cas, en el fitxer .ibdata1.
   
   Per tant els fitxers ibd que no s'han creat en el directori sakila perque hem desactivat el innodb_file_per_table=OFF es troben en el fitxer ibdata1
   
   ![image](https://user-images.githubusercontent.com/61474562/161381773-24593c38-d255-418d-be38-ca99b5e2d368.png)

   
4.    Canvia la configuració del MySQL per:
      - Canviar la localització dels fitxers del tablespace de sistema per defecte a /discs-mysql/
        
        Aturem el servei Mysql:
        
            sudo systemctl stop mysql
        
        ![image](https://user-images.githubusercontent.com/61474562/161381920-9e159cf2-c08c-4ae8-9fb3-eab7d6fc44e9.png)
        
        Creem el directori discs-mysql i li assignem com a propietari l'usuari i grup mysql:
        
            sudo mkdir /discs-mysql
            sudo chown -R mysql:mysql /discs-mysql
            sudo chmod 750 /discs-mysql/

        ![image](https://user-images.githubusercontent.com/61474562/161381973-3b752839-2326-4aab-8948-42436846b5de.png)
        
        copiem recursivament el directori de la base de dades existent a /discs-mysql:
        
            cp -R -p /var/lib/mysql/* /discs-mysql
        
        ![image](https://user-images.githubusercontent.com/61474562/161382006-09230d5b-c316-46c4-b053-57aa076e069a.png)
        
        Editem el fitxer /etc/my.cnf i indiquem el nou directori /discs-mysql i la nova ubicació del socket:
        
        ![image](https://user-images.githubusercontent.com/61474562/161382289-f51a87d5-7ab3-4362-8778-3a4bd9b6ec9d.png)
        
        Iniciem el servei Mysql:
        
            systemctl start mysql

        ![image](https://user-images.githubusercontent.com/61474562/161382310-d44d9bb4-1cce-47b2-a21d-9e1df8de2a16.png)
        
        Comprovem la variable datadir i podem veure que la ubicació és /discs-mysql:
        
            SELECT @@datadir;

        ![image](https://user-images.githubusercontent.com/61474562/161382328-d6bdf703-2ad9-4c59-aa72-9d37b948b9b2.png)
        
      - Tinguem dos fitxers corresponents al tablespace de sistema.
      - Tots dos han de tenir la mateixa mida inicial (10MB) 
      - El tablespace ha de créixer de 5MB en 5MB.
      - Situa aquests fitxers (de manera relativa a la localització per defecte) en una nova localització simulant el següent:
      - /discs-mysql/disk1/primer fitxer de dades → simularà un disc dur
      - /discs-mysql/disk2/segon fitxer de dades → simularà un segon disc dur.
        
        Aturem el servei Mysql:
        
            sudo systemctl stop mysql
        
        ![image](https://user-images.githubusercontent.com/61474562/161381920-9e159cf2-c08c-4ae8-9fb3-eab7d6fc44e9.png)
        
        Creem els directoris /discs-mysql/disk1 /discs-mysql/disk2
        
            sudo mkdir /discs-mysql/disk1
            sudo mkdir /discs-mysql/disk2
            sudo chown -R mysql:mysql /discs-mysql/disk1
            sudo chown -R mysql:mysql /discs-mysql/disk2
            sudo chmod 751 /discs-mysql/disk1
            sudo chmod 751 /discs-mysql/disk2
        
        ![image](https://user-images.githubusercontent.com/61474562/161382962-4d651ea9-3fca-4cf5-adfc-ec2c4b90bab0.png)

        
        
        
        
            innodb_file_per_table=1
            innodb_data_home_dir = /var/lib/mysql/discs-mysql
            innodb_data_file_path=/var/lib/mysql/discs-mysql/disk1/primer:10M;/var/lib/mysql/discs-mysql/disk2/segon:10M:autoextend


