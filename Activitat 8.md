# Activitat 8. Storage Engine MyRocks (1 punt)

• Documenta i posa exemple de com utilitzar ENGINE MyRocks. Crea una Base de dades amb 2 o 3 taules i inserta-hi contingut.
  
  RocksDB es basa en l'arbre de combinació estructurat en registre (o arbre LSM). Està optimitzat per a un emmagatzematge ràpid i combina un espai i una eficiència d'escriptura excepcionals amb un rendiment de lectura acceptable.
  
  Per instal·lar-ho hem de executar la seguent comanda:
  
    yum install Percona-Server-rocksdb-57
  
  Per activar-ho hem de executar la seguent comanda:
  
    ps-admin --enable-rocksdb -u <mysql_admin_user> -p[mysql_admin_pass ]
  
  ![image](https://user-images.githubusercontent.com/61474562/161572593-f39b8d83-3ea6-4ad5-8fc3-e3da6e09f4c1.png)
  
  ![image](https://user-images.githubusercontent.com/61474562/161582041-35452568-5403-4d2f-a9c9-dd2970e30880.png)
  
• Cal documentar els passos que has hagut de realitzar per preparar l'exemple: configuracions, instruccions DML, DDL, etc....
  
  Creació Base de dades ROCKS:
  
    CREATE DATABASE ROCKS;
    SHOW DATABASES;
  
  ![image](https://user-images.githubusercontent.com/61474562/161582146-a0bc4e9d-7428-4871-847c-5c91a287c723.png)
  
  Creació 2 taules ROCKSDB:
  
    USE ROCKS;
    CREATE TABLE prova1 (a INT NOT NULL, b CHAR(15) NOT NULL) ENGINE = RocksDB;
    CREATE TABLE prova2 (a INT NOT NULL, b CHAR(15) NOT NULL) ENGINE = RocksDB;
    
  ![image](https://user-images.githubusercontent.com/61474562/161597007-68c31c11-96c4-40bc-a1cf-952f14d2e3db.png)
  
  Insertem dades a les taules creades anteriorment:
  
    USE ROCKS;
    INSERT INTO prova1 VALUES(1,'dada_uno'),(2,'dada_dos');
    INSERT INTO prova2 VALUES(1,'dada_uno'),(2,'dada_dos');
  
  ![image](https://user-images.githubusercontent.com/61474562/161597528-cb4624ac-05e6-4643-8133-074f2009a324.png)
  
  Comprovació:
  
    SELECT * FROM prova1;
    SELECT * FROM prova2;
    
  ![image](https://user-images.githubusercontent.com/61474562/161597665-e61076fd-36cf-44ef-8512-09d1c9362f17.png)
  
• A quin directori es guarden els fitxers de dades? Fes un llistat de a on són els fitxers i què ocupen.
  
  Els fitxers de dades es guarden en el directori /varlib/mysql/ROCKS/
  
  ![image](https://user-images.githubusercontent.com/61474562/161597957-dd7970f5-fe79-4276-a273-6637d7a0e868.png)
  
• Quina és la compressió per defecte que utilitza per les taules? Com ho faries per canviar-lo. Per exemple utilitza Zlib o ZSTD o sense compressió.
  
  Per comprovar la compressió per defecte hem de executar la seguent consulta:
  
    select * from information_schema.rocksdb_cf_options 
    where option_type like '%ompression%' and cf_name='default';
  
  ![image](https://user-images.githubusercontent.com/61474562/161602707-826978c2-9123-4fb5-94dc-a57d1d012712.png)

  Si volem cambiar el metode de compressió hem de modificar-ho en el fitxer /etc/my.cnf:
  
  En aquest cas el cambiarem al format KZSTD:
  
    rocksdb-override-cf-options='cf1={compression=kZSTD;bottommost_compression=kZSTD;}'
    
  ![image](https://user-images.githubusercontent.com/61474562/161603084-da34e406-dab3-45c9-9fa5-39689830bf96.png)

  Reiniciem el servei MySQL:
  
    systemctl restart mysql
    
  ![image](https://user-images.githubusercontent.com/61474562/161603470-c8df1490-726a-41b6-9f30-2c3840cb6fdf.png)

  Comprovació:
  
     select * from information_schema.rocksdb_cf_options 
     where option_type like '%ompression%' and cf_name='default';
  
  ![image](https://user-images.githubusercontent.com/61474562/161604200-acf6fe99-eb12-451b-8469-22b2d67e2b61.png)
