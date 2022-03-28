**CFGS Administració de Sistemes Informàtics a la Xarxa**

**Mòdul 10:** Administració de sistemes gestors de base de dades (ASIX)

**UF 1:** Llenguatges SQL: DCL i extensió procedimental SGBD corporatiu


***


**Activitat 2: ConfiguracioLogs**


***

**Gaurav Pal**

**Ahmed Belhadi**

**ASIX**

**29/03/2022**
***

# **[Configuració i comprovació de logs]** ![Interfaz de usuario gráfica, Texto, Aplicación Descripción generada     automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/logs.png)


***

1.Quins són els logs activats per defecte? Crea un fitxer de
configuració anomenat logs.cnf a on:

El log activat per defecte es el log binari, que ve activat per defecte
per veure ho tenim que anar a mysql .

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image1.png)

I introduïm la sentencia per veure les variables log , com es veu en la
captura el log_bin esta activat per defecte

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image2.png)

I en esta captura utilitzant la sentencia per mostrar variables, veiem
que el general log i el slow query estan desactivats

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image3.png)

Per crear el arxiu de configuració logs.cnf primer de tot creem una nova
carpeta anomenada percona-server

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image4.png)

I creem el arxiu de configuració guardem y sortim.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image5.png)

Anem al arxiu de configuració my.cnf i tenim que fer un includedir per
que el arxiu de configuracio logs.cnf no el llegeix el mysql i per tant
no es podrà activar els logs . Es per això que a dins del arxiu de
configuració my.cnf com es veu en la captura incloem la ruta de la
carpeta que hem creat i guardem, així ens deixarà posar paràmetres que
els llegirà el mysql.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image6.png)

Ara anem a la ruta on esta el arxiu de configuració logs.cnf .

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image7.png)

Una vegada ja estem a dins del arxiu de configuració logs.cnf modifiquem
el arxiu logs.cnf posem entre claudàtors mysqld i activem el log General
,el log Slow Query i long query_time per que guardi registres que durin
mes de 2 segons no modifiquem el log binari ja que ve activat per
defecte .

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image8.png)

Anem al mysql

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image1.png)

Fem la sentencia show variables i veiem que efectivament esta activat el
slow querry i el general

![Texto Descripción generada automáticamente con confianza
media](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image9.png)

Per anar a la ruta de el general log tenim que anar a la següent ruta i
el que esta marcat es el arxiu on esta tots els logs de el general log.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image10.png)

Per anar a la ruta de el binary log tenim que anar a la mateixa ruta que
abans i es el que esta marcat son els arxius on estan els logs de el
binary log

![Captura de pantalla con letras Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image11.png)

Per anar a la ruta de el Slow Query log tenim que anar un altra vegada a
la mateixa ruta que abans i el que esta marcat es el fitxer on es guarda
els logs de la Slow Query.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image12.png)

2\. Comprova l\'estat de les opcions de log que has utilitzat mitjançant
una sessió de mysql client.

![Interfaz de usuario gráfica, Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image13.png)

3\. Modifica el fitxer de configuració i desactiva els logs de binary,
slow query i genral. Nota: Simplament desactiva\'ls no borris altres
paràmetres com la ruta dels fitxers, etc\...

Per modificar el fitxer de configuració i desactivar els logs de binary,
slow query i general anem a la ruta on esta el fitxer de logs.cnf.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image14.png)

I a dins del arxiu de configuració logs.cnf desactivem el general log
posant ho a OFF, el slow query li posem un 0 i per desactivar el log
binary posem el paràmetre "disable_log_bin" i ho guardem.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image15.png)

Reiniciem el servei de mysql.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image16.png)

Entrem al mysql

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image17.png)

Utilitzem la sentencia per veure si esta desactivat el slow Query i el
General, veiem que ja estan desactivats.

![Texto Descripción generada automáticamente con confianza
baja](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image18.png)

Per el binary log utilitzarem aquesta sentencia per veure si esta
desactivat el binary, veiem que log_bin esta desactivat.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image19.png)

4\. Activa els logs en temps d\'execució mitjançant la sentència SET
GLOBAL. També canvia el destí de log general a una taula (paràmetre
log_output). Quines són les sentències que has utilitzat? A quina taula
es guarden els dels del general log?

Primer anem al mysql

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image17.png)

Ara farem servir la sentencia SET GLOBAL per activar el general log

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image20.png)

I també el mateix procediment per activar el slow query

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image21.png)

Una vegada ja activats fem servir sentencia SHOW GLOBAL per veure si
estan activats i com es veu estan activats.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image22.png)

Per activar el log_bin tenim que anar al arxiu de configuració ja que no
es pot fer amb el SET GLOBAL i per eliminar-ho tenim que anar a la ruta
del arxiu de configuració logs.cnf

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image7.png)

Modifiquem el arxiu de configuració logs.cnf , eliminem el paràmetre
"disable_bin_log" i guadem.

![Imagen en blanco y negro Descripción generada automáticamente con
confianza
media](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image23.png)

Tornem al mysql

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image1.png)

Fem servir sentencia SHOW GLOBAL per veure si esta activat i com es veu
estan activats.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image24.png)

Per canviar el log_output a TABLE primer tenim que anar al arxiu de
configuració logs.cnf

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image7.png)

I a dins del arxiu de configuració afegim el paràmetre log_output=TABLE
i ho guardem .

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image25.png)

Ara anem al mysql

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image1.png)

Utilitzarem aquesta sentencia per veure si el value es TABLE i es veu
que si ha canviat a table.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image26.png)

La taula on es guarden els logs generals es en "mysql.general_log" tenim
que utilitzar la sentencia següent per veure el que conte.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image27.png)

5\. Carrega la BD Sakila localitzada a la web de o Descarrega\'t el
fitxer sakila-schema.sql del Moodle. o carrega la BD dins del MySQL
utilitzant la sentència:

Per descarregar la base de dades de Sakila primer anem al link següent
[MySQL :: Other MySQL
Documentation](https://dev.mysql.com/doc/index-other.html), anem a
example Datebases.

![Tabla Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image28.png)

Li donem click dret i copiar vinculo

![Interfaz de usuario gráfica, Texto, Aplicación Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image29.png)

Una vegada ja hem copiat el vincle fem wget , posem la el vincle li
donem al enter i descarragem el archiu tar en la carpeta creada sakila a
la ruta /home/sakila .

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image30.png)

Descomprimim el arxiu tar i es veu que tenim la carpeta sakila-db.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image31.png)

Anem al mysql

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image1.png)

Utilitzem aquesta sentencia per instal·lar el sakila-schema.sql.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image32.png)

Utilitzem USE Skila per utilitzar la base de dades.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image33.png)

Mostrem les taules que te la base de dades de Sakila.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image34.png)

6\. Compte el numero de sentències CREATE TABLE dins del general log
mitjançant una sentencia SQL.

Per contar quantes sentencies CREATE TABLE hi ha en la taula
"mysql.general_log" tenim que utilitzar aquesta sentencia mysql i
utilitzem el convert per desencriptar els arguments .

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image35.png)

Com es veu hi ha 24 sentencies CREATE TABLE en la taula
"mysql.general_log".

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image36.png)

7\. Executa una query mitjançant la funció SLEEP(11) per tal de que es
guardi en el log de Slow Query Log. Mostra el contingut del log
demostrant-ho.

Primer anem al mysql

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image1.png)

Utilitzarem la sentencia SELECT SLEEP(11) per que es dormi durant 11
segons.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image37.png)

Per comprovar que la sentencia que ha durant 11 segons esta a dins de la
taula de Slow Query

Fem la següent sentencia SELECT per veure que ha guardat el log del
SLEEP, com es veu esta guardat i ha durant 11 segons

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image38.png)

8\. Assegura\'t que el Binary Log estigui activat i borra tots els logs
anteriors mitjançant la sentència RESET MASTER.

Primer ens assegurem que tenim el log_bin activat. Utilitzarem aquesta
sentencia per veure si esta activat i com es veu a la captura si esta
activat.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image39.png)

Entrem al mysql

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image1.png)

Utilitzem la següent sentencia per eliminar tots els arxius binlog

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image40.png)

Com es veu a eliminat tots els arxius binlog i ha creat un de nou
anomenat "binlog.000001".

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image41.png)

Creem la base de dades foo i la eliminem amb la següent sentencia.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image42.png)

Utilitzem la sentencia SHOW BINLOG EVENTS per mostrar els canvis que hi
ha en el arxiu binlog.000001, com es veu les sentencies CREATE TABLE i
DROP DATABASE estan registrades en el apartat de info en el arxiu
binlog.000001.

![Imagen que contiene Interfaz de usuario gráfica Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image43.png)

Per realitzar un rotate log utilitzarem la sentencia FLUSH LOGS.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image44.png)

El que fa aquesta sentencia es crear un nou fitxer binlog

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image45.png)

Creem una base de dades anomenada bar i la eliminem.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image46.png)

Per mostrar la llista de binlogs i també veure els últims canvis tenim
que utilitzar tres sentencies. Primer utilitzem aquesta sentencia per
veure els canvis que hi ha en el binlog.000001.

![Interfaz de usuario gráfica Descripción generada automáticamente con
confianza
media](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image47.png)

Ara utilitzarem aquesta sentencia per veure el que conte el
binlog.000002 i com es veu ha quedat enregistrat DROP DATABASE bar i
CREATE DATABASE bar en el fitxer binlog.000002.

![Texto Descripción generada automáticamente con confianza
media](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image48.png)

Per veure tota la llista de fitxers binlog utilitzarem aquesta sentencia
per veure tots el fitxers binlog.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image49.png)

Per eliminar el primer binlog tenim que utilitzar la següent sentencia
posant el binlog.000002 per poder eliminar el primer.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image50.png)

Com veiem en aquesta captura ha quedat eliminat el binlog.000001.

![Texto, Escala de tiempo Descripción generada automáticamente con
confianza
media](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image51.png)

Per poder utilitzar el programa mysqlbinlog tenim que sortir del mysql i
utilitzar la següent comanda en la ruta on esta el fitxer guardat.
Primer anem a la ruta del fitxer

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image52.png)

Ara utilitzem la sentencia següent per accedir a dins del arxiu
logbin.000002

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image53.png)

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image54.png) 
Com es veu a dins del fitxer s'
enregistren molta informacio la mes rellevant es que ha guardat les dues
sentencies CREATE TABLE bar i DROP TABLE bar

Per saber el numero de event que es el CREATE TABLE bar a dins del
fitxer veiem que posa at 233 es el numero de event del create table
juntament amb mes sentencies.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image55.png)

9\. De quina manera podem desactivar el binary log només d'una sessió en
concret. Imagina't que ets un administrador de la BD i no vols que les
instruccions que facis es gravin en el binary_log.

Per pode desactivar el el log_bin de una sessio en concret tenim que
desactivar el sql_log_bin per poder fer qualsevol sentencia sense que es
guardi en el arxiu logbin

Primer tenim que anar al mysql

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image1.png)

Una vegada a dins del mysql utilitzarem la seguent sentencia per
desactivar el log_bin per aquesta sessio

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image56.png)

Comprovem amb aquesta sentencia que esta desactivat i veiem que esta
desactivat.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image57.png)

Per comprovar que la sentencia crearem una base de dades y la eliminarem

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image58.png)

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image59.png)
Ara utilitzarem la sentencia binlog per
veure que no queda enregistrat EL CREATE TABLE hola i DROP DATABASE
hola, com es veu en la captura no ha quedat enregistrat.

