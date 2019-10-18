# SO_AWJF_StatischeWaldgrenzen
Frickel-DB:
```
docker run --rm --name edit-db -p 54321:5432 --hostname primary \
-e PG_DATABASE=edit -e PG_PRIMARY_PORT=5432 -e PG_MODE=primary \
-e PG_USER=admin -e PG_PASSWORD=admin \
-e PG_PRIMARY_USER=repl -e PG_PRIMARY_PASSWORD=repl \
-e PG_ROOT_PASSWORD=secret \
-e PG_WRITE_USER=gretl -e PG_WRITE_PASSWORD=gretl \
-e PG_READ_USER=ogc_server -e PG_READ_PASSWORD=ogc_server \
sogis/oereb-db
```



```
java -jar /Users/stefan/apps/ili2pg-4.3.0/ili2pg-4.3.0.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --nameByTopic --strokeArcs --createFk --createEnumTabsWithId --modeldir ".;http://models.geo.admin.ch" --models SO_AWJF_StatischeWaldgrenzen_20191017 --dbschema awjf_waldgrenzen_02 --schemaimport
```

## 01
```
INSERT INTO 
    awjf_waldgrenzen_01.geobasisdaten_typ (t_type, t_ili_tid, acode, bezeichnung, abkuerzung, verbindlichkeit, bemerkungen, art, kt_nummer)
VALUES('so_wjf_0191017geobasisdaten_typ', uuid_generate_v4(), '1', '1', '1', 31, '1', 1, 'kantonsnummer');

INSERT INTO 
    awjf_waldgrenzen_01.geobasisdaten_typ (t_type, t_ili_tid, acode, bezeichnung, abkuerzung, verbindlichkeit, bemerkungen, art, kt_nummer)
VALUES('geobasisdaten_typ', uuid_generate_v4(), '2', '2', '2', 31, '2', 2, '');
```

```
java -jar /Users/stefan/apps/ili2pg-4.3.0/ili2pg-4.3.0.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --nameByTopic --strokeArcs --createFk --createEnumTabsWithId --modeldir ".;http://models.geo.admin.ch" --models SO_AWJF_StatischeWaldgrenzen_20191017 --exportModels SO_AWJF_StatischeWaldgrenzen_20191017 --dbschema awjf_waldgrenzen_01 --disableValidation --export so.xtf

-> Daten mit t_type=so_wjf_0191017geobasisdaten_typ im SO-Modell

java -jar /Users/stefan/apps/ili2pg-4.3.0/ili2pg-4.3.0.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --nameByTopic --strokeArcs --createFk --createEnumTabsWithId --modeldir ".;http://models.geo.admin.ch" --models SO_AWJF_StatischeWaldgrenzen_20191017 --exportModels Waldgrenzen_LV95_V1_1 --dbschema awjf_waldgrenzen_01 --disableValidation --export so.xtf

-> Daten mit t_type=so_wjf_0191017geobasisdaten_typ im Bundesmodell

java -jar /Users/stefan/apps/ili2pg-4.3.0/ili2pg-4.3.0.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --nameByTopic --strokeArcs --createFk --createEnumTabsWithId --modeldir ".;http://models.geo.admin.ch" --models Waldgrenzen_LV95_V1_1 --exportModels SO_AWJF_StatischeWaldgrenzen_20191017 --dbschema awjf_waldgrenzen_01 --disableValidation --export ch.xtf

-> Fehler: unkown model. Vom Bundesmodell ins  Kantonsmodell geht nicht.

java -jar /Users/stefan/apps/ili2pg-4.3.0/ili2pg-4.3.0.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --nameByTopic --strokeArcs --createFk --createEnumTabsWithId --modeldir ".;http://models.geo.admin.ch" --models Waldgrenzen_LV95_V1_1 --exportModels Waldgrenzen_LV95_V1_1 --dbschema awjf_waldgrenzen_01 --disableValidation --export ch.xtf

-> Daten mit beiden t_type im Bundesmodell.
```

## 02
```
INSERT INTO 
    awjf_waldgrenzen_02.geobasisdaten_typ (t_type, t_ili_tid, acode, bezeichnung, abkuerzung, verbindlichkeit, bemerkungen, art, kt_nummer)
VALUES('geobasisdaten_typ_kt', uuid_generate_v4(), '1', '1', '1', 172, '1', 140, 'kantonsnummer');

INSERT INTO 
    awjf_waldgrenzen_02.geobasisdaten_typ (t_type, t_ili_tid, acode, bezeichnung, abkuerzung, verbindlichkeit, bemerkungen, art, kt_nummer)
VALUES('geobasisdaten_typ', uuid_generate_v4(), '2', '2', '2', 172, '2', 140, '');
```

```
java -jar /Users/stefan/apps/ili2pg-4.3.0/ili2pg-4.3.0.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --nameByTopic --strokeArcs --createFk --createEnumTabsWithId --modeldir ".;http://models.geo.admin.ch" --models SO_AWJF_StatischeWaldgrenzen_20191017 --exportModels SO_AWJF_StatischeWaldgrenzen_20191017 --dbschema awjf_waldgrenzen_02 --disableValidation --export so.xtf

-> Daten mit beiden t_typen werden exportiert.

java -jar /Users/stefan/apps/ili2pg-4.3.0/ili2pg-4.3.0.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --nameByTopic --strokeArcs --createFk --createEnumTabsWithId --modeldir ".;http://models.geo.admin.ch" --models SO_AWJF_StatischeWaldgrenzen_20191017 --exportModels Waldgrenzen_LV95_V1_1 --dbschema awjf_waldgrenzen_02 --disableValidation --export so.xtf

-> Daten mit beiden t_type werden ins Bundesmodell exportiert.

java -jar /Users/stefan/apps/ili2pg-4.3.0/ili2pg-4.3.0.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --nameByTopic --strokeArcs --createFk --createEnumTabsWithId --modeldir ".;http://models.geo.admin.ch" --models Waldgrenzen_LV95_V1_1 --exportModels SO_AWJF_StatischeWaldgrenzen_20191017 --dbschema awjf_waldgrenzen_02 --disableValidation --export ch.xtf

-> Fehler: unkown model. Vom Bundesmodell ins  Kantonsmodell geht nicht.

java -jar /Users/stefan/apps/ili2pg-4.3.0/ili2pg-4.3.0.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --nameByTopic --strokeArcs --createFk --createEnumTabsWithId --modeldir ".;http://models.geo.admin.ch" --models Waldgrenzen_LV95_V1_1 --exportModels Waldgrenzen_LV95_V1_1 --dbschema awjf_waldgrenzen_02 --disableValidation --export ch.xtf

-> Daten mit beiden t_type im Bundesmodell. Unterschied zu (2)? Warum nicht bloss "Bundes-Objekt"?
```
