## Indica quins són els motors d’emmagatzematge que pots utilitzar (quins estan actius)? Mostra la comanda utilitzada i el resultat d’aquesta.
    mysql> show storage engines;
   A l'imatge ens mostra el motor que esta per defecte i els motors disponibles.
   ![image](https://user-images.githubusercontent.com/61474562/157503356-c1cea5e2-9d4d-46d1-8ca1-d52a0a593029.png)


## Com puc saber quin és el motor d’emmagatzematge per defecte. Mostra com canviar aquest paràmetre de tal manera que les noves taules que creem a la BD per defecte utilitzin el motor MyISAM?
   El motor d’emmagatzematge per defecte és InnoDB com ens indica a la taula.
   ![image](https://user-images.githubusercontent.com/61474562/157504081-30c00496-4a46-4c05-b48e-a55b9111f56d.png)
   Per posar per defecte el motor MyISAM hem de introduir el seguent:
   
    mysql> SET @@storage_engine=MyISAM;
   Com podem comprovar en la imatge, el motor per defecte és MyISAM
   ![image](https://user-images.githubusercontent.com/61474562/157506017-a2d0261a-5001-46de-b616-4c19b81cb064.png)


## Explica els passos per instal·lar i activar l'ENGINE MyRocks. MyRocks és un motor d'emmagatzematge per MySQL basat en RocksDB (SGBD incrustat de tipus clau-valor). Aquest tipus d’emmagatzematge està optimitzat per ser molt eficient en les escriptures amb lectures acceptables.
   Per instal·lar i activar l'Engine MyRocks hem de descarregar el paquet:
    
    $ sudo yum install percona-server-rocksdb
   Després hem d'executar el seguent script:
    
    $ ps-admin --enable-rocksdb -u <mysql_admin_user> -p[mysql_admin_pass]
   Comprovem que s'hagi instal·lat i activat:
   ![image](https://user-images.githubusercontent.com/61474562/157510018-8278a05a-f050-43a2-93f2-00ffbb354396.png)
   
## Importa la BD Sakila com a taules MyISAM. Fes els canvis necessaris per importar la BD Sakila perquè totes les taules siguin de tipus MyISAM. Mira quins són els fitxers físics que ha creat, quan ocupen i quines són les seves extensions. Mostra'n una captura de pantalla i indica què conté cada fitxer. Un cop fet això torna a deixar el motor InnoDB per defecte.
   Hem de substituir la paraula InnoDB de l'script per MyISAM i farem que totes les taules siguin MyISAM
   ![image](https://user-images.githubusercontent.com/61474562/157512373-359836d4-b8fa-4231-a5be-290c4c4afb98.png)
   
   Els Fitxers de les taules es troben a la seguent ruta:
   
    cd /var/lib/mysql/sakila/
   ![image](https://user-images.githubusercontent.com/61474562/157514239-7f102e9c-72a8-4b42-934f-d373f2be9341.png)
   Per comprovar el espai dels fitxers fem la comanda:
    
    ls -l
   ![image](https://user-images.githubusercontent.com/61474562/157514450-477bb911-5c8c-485c-a1be-d3a6ac0635a3.png)
   Com podem observar, per cada taula ens ha creat 3 fitxers.
### .sdi
   Conté totes les metadades de la taula:
   ![image](https://user-images.githubusercontent.com/61474562/157515235-d4fac947-ac93-4e49-9a21-de863f992914.png)

### .MYD
   Conté les dades de la taula:
   
   ![image](https://user-images.githubusercontent.com/61474562/157515699-b01b6334-9193-470d-80a0-0c66215c1d29.png)

### .MYI
   És el fitxer d'indexació de la taula i no podem veure el seu contingut:
   
   ![image](https://user-images.githubusercontent.com/61474562/157515929-c60c6ffb-b8ea-4430-ad29-07a89d62cf8b.png)

   
## A partir de MySQL apareixen els schemas de metadades i informació guardats amb InnoDB. Busca informació d'aquests schemas. Indica quin és l'objectiu de cadascun d'ells i posa'n un exemple d'ús.

## Posa un exemple que produeix un DEADLOCK i mostra-ho al professor.
