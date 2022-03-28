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

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image1.png){width="3.34375in"
height="0.3854166666666667in"}

I introduïm la sentencia per veure les variables log , com es veu en la
captura el log_bin esta activat per defecte

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image2.png){width="5.905555555555556in"
height="4.5152777777777775in"}

I en esta captura utilitzant la sentencia per mostrar variables, veiem
que el general log i el slow query estan desactivats

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image3.png){width="5.1875in"
height="2.59375in"}

Per crear el arxiu de configuració logs.cnf primer de tot creem una nova
carpeta anomenada percona-server

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image4.png){width="5.610239501312336in"
height="0.3652504374453193in"}

I creem el arxiu de configuració guardem y sortim.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image5.png){width="6.536058617672791in"
height="0.3167257217847769in"}

Anem al arxiu de configuració my.cnf i tenim que fer un includedir per
que el arxiu de configuracio logs.cnf no el llegeix el mysql i per tant
no es podrà activar els logs . Es per això que a dins del arxiu de
configuració my.cnf com es veu en la captura incloem la ruta de la
carpeta que hem creat i guardem, així ens deixarà posar paràmetres que
els llegirà el mysql.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image6.png){width="5.905555555555556in"
height="2.9364315398075242in"}

Ara anem a la ruta on esta el arxiu de configuració logs.cnf .

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image7.png){width="4.708333333333333in"
height="0.46875in"}

Una vegada ja estem a dins del arxiu de configuració logs.cnf modifiquem
el arxiu logs.cnf posem entre claudàtors mysqld i activem el log General
,el log Slow Query i long query_time per que guardi registres que durin
mes de 2 segons no modifiquem el log binari ja que ve activat per
defecte .

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image8.png){width="5.905555555555556in"
height="3.567361111111111in"}

Anem al mysql

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image1.png){width="3.34375in"
height="0.3854166666666667in"}

Fem la sentencia show variables i veiem que efectivament esta activat el
slow querry i el general

![Texto Descripción generada automáticamente con confianza
media](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image9.png){width="5.5625in"
height="2.9895833333333335in"}

Per anar a la ruta de el general log tenim que anar a la següent ruta i
el que esta marcat es el arxiu on esta tots els logs de el general log.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image10.png){width="5.905555555555556in"
height="1.9027777777777777in"}

Per anar a la ruta de el binary log tenim que anar a la mateixa ruta que
abans i es el que esta marcat son els arxius on estan els logs de el
binary log

![Captura de pantalla con letras Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image11.png){width="5.905555555555556in"
height="1.9236111111111112in"}

Per anar a la ruta de el Slow Query log tenim que anar un altra vegada a
la mateixa ruta que abans i el que esta marcat es el fitxer on es guarda
els logs de la Slow Query.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image12.png){width="5.905555555555556in"
height="1.875in"}

2\. Comprova l\'estat de les opcions de log que has utilitzat mitjançant
una sessió de mysql client.

![Interfaz de usuario gráfica, Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image13.png){width="5.905555555555556in"
height="2.7881944444444446in"}

3\. Modifica el fitxer de configuració i desactiva els logs de binary,
slow query i genral. Nota: Simplament desactiva\'ls no borris altres
paràmetres com la ruta dels fitxers, etc\...

Per modificar el fitxer de configuració i desactivar els logs de binary,
slow query i general anem a la ruta on esta el fitxer de logs.cnf.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image14.png){width="4.802083333333333in"
height="0.2916666666666667in"}

I a dins del arxiu de configuració logs.cnf desactivem el general log
posant ho a OFF, el slow query li posem un 0 i per desactivar el log
binary posem el paràmetre "disable_log_bin" i ho guardem.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image15.png){width="5.905555555555556in"
height="3.191666666666667in"}

Reiniciem el servei de mysql.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image16.png){width="5.010416666666667in"
height="0.3645833333333333in"}

Entrem al mysql

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image17.png){width="5.905555555555556in"
height="2.40625in"}

Utilitzem la sentencia per veure si esta desactivat el slow Query i el
General, veiem que ja estan desactivats.

![Texto Descripción generada automáticamente con confianza
baja](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image18.png){width="5.905555555555556in"
height="3.283333333333333in"}

Per el binary log utilitzarem aquesta sentencia per veure si esta
desactivat el binary, veiem que log_bin esta desactivat.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image19.png){width="4.98122375328084in"
height="2.6516940069991253in"}

4\. Activa els logs en temps d\'execució mitjançant la sentència SET
GLOBAL. També canvia el destí de log general a una taula (paràmetre
log_output). Quines són les sentències que has utilitzat? A quina taula
es guarden els dels del general log?

Primer anem al mysql

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image17.png){width="5.548266622922135in"
height="2.2606714785651794in"}

Ara farem servir la sentencia SET GLOBAL per activar el general log

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image20.png){width="3.3020833333333335in"
height="0.5in"}

I també el mateix procediment per activar el slow query

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image21.png){width="3.4166666666666665in"
height="0.5in"}

Una vegada ja activats fem servir sentencia SHOW GLOBAL per veure si
estan activats i com es veu estan activats.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image22.png){width="5.905555555555556in"
height="3.2402777777777776in"}

Per activar el log_bin tenim que anar al arxiu de configuració ja que no
es pot fer amb el SET GLOBAL i per eliminar-ho tenim que anar a la ruta
del arxiu de configuració logs.cnf

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image7.png){width="4.708333333333333in"
height="0.46875in"}

Modifiquem el arxiu de configuració logs.cnf , eliminem el paràmetre
"disable_bin_log" i guadem.

![Imagen en blanco y negro Descripción generada automáticamente con
confianza
media](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image23.png){width="5.905555555555556in"
height="1.6722222222222223in"}

Tornem al mysql

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image1.png){width="3.34375in"
height="0.3854166666666667in"}

Fem servir sentencia SHOW GLOBAL per veure si esta activat i com es veu
estan activats.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image24.png){width="5.905555555555556in"
height="1.8930555555555555in"}

Per canviar el log_output a TABLE primer tenim que anar al arxiu de
configuració logs.cnf

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image7.png){width="4.708333333333333in"
height="0.46875in"}

I a dins del arxiu de configuració afegim el paràmetre log_output=TABLE
i ho guardem .

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image25.png){width="5.905555555555556in"
height="1.3166666666666667in"}

Ara anem al mysql

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image1.png){width="3.34375in"
height="0.3854166666666667in"}

Utilitzarem aquesta sentencia per veure si el value es TABLE i es veu
que si ha canviat a table.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image26.png){width="4.85162510936133in"
height="1.749757217847769in"}

La taula on es guarden els logs generals es en "mysql.general_log" tenim
que utilitzar la sentencia següent per veure el que conte.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image27.png){width="5.905555555555556in"
height="4.846527777777778in"}

5\. Carrega la BD Sakila localitzada a la web de o Descarrega\'t el
fitxer sakila-schema.sql del Moodle. o carrega la BD dins del MySQL
utilitzant la sentència:

Per descarregar la base de dades de Sakila primer anem al link següent
[MySQL :: Other MySQL
Documentation](https://dev.mysql.com/doc/index-other.html), anem a
example Datebases.

![Tabla Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image28.png){width="5.905555555555556in"
height="2.1847222222222222in"}

Li donem click dret i copiar vinculo

![Interfaz de usuario gráfica, Texto, Aplicación Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image29.png){width="5.905555555555556in"
height="3.876388888888889in"}

Una vegada ja hem copiat el vincle fem wget , posem la el vincle li
donem al enter i descarragem el archiu tar en la carpeta creada sakila a
la ruta /home/sakila .

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image30.png){width="5.905555555555556in"
height="1.3944444444444444in"}

Descomprimim el arxiu tar i es veu que tenim la carpeta sakila-db.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image31.png){width="5.905555555555556in"
height="0.5409722222222222in"}

Anem al mysql

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image1.png){width="3.34375in"
height="0.3854166666666667in"}

Utilitzem aquesta sentencia per instal·lar el sakila-schema.sql.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image32.png){width="5.905555555555556in"
height="3.3402777777777777in"}

Utilitzem USE Skila per utilitzar la base de dades.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image33.png){width="5.864583333333333in"
height="0.9166666666666666in"}

Mostrem les taules que te la base de dades de Sakila.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image34.png){width="2.800579615048119in"
height="3.948899825021872in"}

6\. Compte el numero de sentències CREATE TABLE dins del general log
mitjançant una sentencia SQL.

Per contar quantes sentencies CREATE TABLE hi ha en la taula
"mysql.general_log" tenim que utilitzar aquesta sentencia mysql i
utilitzem el convert per desencriptar els arguments .

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image35.png){width="5.905555555555556in"
height="0.2152777777777778in"}

Com es veu hi ha 24 sentencies CREATE TABLE en la taula
"mysql.general_log".

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image36.png){width="5.905555555555556in"
height="1.0583333333333333in"}

7\. Executa una query mitjançant la funció SLEEP(11) per tal de que es
guardi en el log de Slow Query Log. Mostra el contingut del log
demostrant-ho.

Primer anem al mysql

![](./images//media/image1.png){width="3.34375in"
height="0.3854166666666667in"}

Utilitzarem la sentencia SELECT SLEEP(11) per que es dormi durant 11
segons.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image37.png){width="2.9895833333333335in"
height="1.6979166666666667in"}

Per comprovar que la sentencia que ha durant 11 segons esta a dins de la
taula de Slow Query

Fem la següent sentencia SELECT per veure que ha guardat el log del
SLEEP, com es veu esta guardat i ha durant 11 segons

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image38.png){width="5.905555555555556in"
height="3.4770833333333333in"}

8\. Assegura\'t que el Binary Log estigui activat i borra tots els logs
anteriors mitjançant la sentència RESET MASTER.

Primer ens assegurem que tenim el log_bin activat. Utilitzarem aquesta
sentencia per veure si esta activat i com es veu a la captura si esta
activat.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image39.png){width="5.75in"
height="2.0in"}

Entrem al mysql

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image1.png){width="3.34375in"
height="0.3854166666666667in"}

Utilitzem la següent sentencia per eliminar tots els arxius binlog

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image40.png){width="3.5104166666666665in"
height="0.7291666666666666in"}

Com es veu a eliminat tots els arxius binlog i ha creat un de nou
anomenat "binlog.000001".

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image41.png){width="3.625in"
height="1.5520833333333333in"}

Creem la base de dades foo i la eliminem amb la següent sentencia.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image42.png){width="3.9166666666666665in"
height="1.3020833333333333in"}

Utilitzem la sentencia SHOW BINLOG EVENTS per mostrar els canvis que hi
ha en el arxiu binlog.000001, com es veu les sentencies CREATE TABLE i
DROP DATABASE estan registrades en el apartat de info en el arxiu
binlog.000001.

![Imagen que contiene Interfaz de usuario gráfica Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image43.png){width="5.905555555555556in"
height="1.445138888888889in"}

Per realitzar un rotate log utilitzarem la sentencia FLUSH LOGS.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image44.png){width="3.6041666666666665in"
height="0.7395833333333334in"}

El que fa aquesta sentencia es crear un nou fitxer binlog

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image45.png){width="4.25in"
height="1.8020833333333333in"}

Creem una base de dades anomenada bar i la eliminem.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image46.png){width="3.46875in"
height="1.2604166666666667in"}

Per mostrar la llista de binlogs i també veure els últims canvis tenim
que utilitzar tres sentencies. Primer utilitzem aquesta sentencia per
veure els canvis que hi ha en el binlog.000001.

![Interfaz de usuario gráfica Descripción generada automáticamente con
confianza
media](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image47.png){width="5.905555555555556in"
height="1.5027777777777778in"}

Ara utilitzarem aquesta sentencia per veure el que conte el
binlog.000002 i com es veu ha quedat enregistrat DROP DATABASE bar i
CREATE DATABASE bar en el fitxer binlog.000002.

![Texto Descripción generada automáticamente con confianza
media](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image48.png){width="5.905555555555556in"
height="1.5805555555555555in"}

Per veure tota la llista de fitxers binlog utilitzarem aquesta sentencia
per veure tots el fitxers binlog.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image49.png){width="4.03125in"
height="1.6979166666666667in"}

Per eliminar el primer binlog tenim que utilitzar la següent sentencia
posant el binlog.000002 per poder eliminar el primer.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image50.png){width="3.9895833333333335in"
height="0.4583333333333333in"}

Com veiem en aquesta captura ha quedat eliminat el binlog.000001.

![Texto, Escala de tiempo Descripción generada automáticamente con
confianza
media](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image51.png){width="3.5520833333333335in"
height="1.53125in"}

Per poder utilitzar el programa mysqlbinlog tenim que sortir del mysql i
utilitzar la següent comanda en la ruta on esta el fitxer guardat.
Primer anem a la ruta del fitxer

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image52.png){width="3.6666666666666665in"
height="0.40625in"}

Ara utilitzem la sentencia següent per accedir a dins del arxiu
logbin.000002

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image53.png){width="4.979166666666667in"
height="0.25in"}

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image54.png){width="7.635416666666667in"
height="5.303472222222222in"} Com es veu a dins del fitxer s'
enregistren molta informacio la mes rellevant es que ha guardat les dues
sentencies CREATE TABLE bar i DROP TABLE bar

Per saber el numero de event que es el CREATE TABLE bar a dins del
fitxer veiem que posa at 233 es el numero de event del create table
juntament amb mes sentencies.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image55.png){width="7.964373359580052in"
height="2.5520833333333335in"}

9\. De quina manera podem desactivar el binary log només d'una sessió en
concret. Imagina't que ets un administrador de la BD i no vols que les
instruccions que facis es gravin en el binary_log.

Per pode desactivar el el log_bin de una sessio en concret tenim que
desactivar el sql_log_bin per poder fer qualsevol sentencia sense que es
guardi en el arxiu logbin

Primer tenim que anar al mysql

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image1.png){width="3.34375in"
height="0.3854166666666667in"}

Una vegada a dins del mysql utilitzarem la seguent sentencia per
desactivar el log_bin per aquesta sessio

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image56.png){width="3.2708333333333335in"
height="0.71875in"}

Comprovem amb aquesta sentencia que esta desactivat i veiem que esta
desactivat.

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image57.png){width="3.8020833333333335in"
height="1.21875in"}

Per comprovar que la sentencia crearem una base de dades y la eliminarem

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image58.png){width="3.9283114610673664in"
height="1.2405194663167105in"}

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image59.png){width="6.969444444444444in"
height="1.8770833333333334in"}Ara utilitzarem la sentencia binlog per
veure que no queda enregistrat EL CREATE TABLE hola i DROP DATABASE
hola, com es veu en la captura no ha quedat enregistrat.

