# Activitat 8. Storage Engine MyRocks (1 punt)

• Documenta i posa exemple de com utilitzar ENGINE MyRocks. Crea una Base de dades amb 2 o 3 taules i inserta-hi contingut.
  
  RocksDB es basa en l'arbre de combinació estructurat en registre (o arbre LSM). Està optimitzat per a un emmagatzematge ràpid i combina un espai i una eficiència d'escriptura excepcionals amb un rendiment de lectura acceptable.
  
  Per instal·lar-ho hem de executar la seguent comanda:
  
    yum install Percona-Server-rocksdb-57
  
  Per activar-ho hem de executar la seguent comanda:
  
    ps-admin --enable-rocksdb -u <mysql_admin_user> -p[mysql_admin_pass ]
  
  ![image](https://user-images.githubusercontent.com/61474562/161572593-f39b8d83-3ea6-4ad5-8fc3-e3da6e09f4c1.png)
  
• Cal documentar els passos que has hagut de realitzar per preparar l'exemple: configuracions, instruccions DML, DDL, etc....
  
  
• A quin directori es guarden els fitxers de dades? Fes un llistat de a on són els fitxers i què ocupen.
  
  
• Quina és la compressió per defecte que utilitza per les taules? Com ho faries per canviar-lo. Per exemple utilitza Zlib o ZSTD o sense compressió.
  
  
