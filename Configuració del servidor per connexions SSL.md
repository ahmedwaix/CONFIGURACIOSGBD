**CFGS Administració de Sistemes Informàtics a la Xarxa**

**Mòdul 10:** Administració de sistemes gestors de base de dades (ASIX)

**UF 1:** Llenguatges SQL: DCL i extensió procedimental SGBD corporatiu


***


**Activitat 2: Configuració Logs**


***

**Gaurav Pal**

**Ahmed Belhadi**

**ASIX**

**01/04/2022**
***

# **[Configuració del servidor per connexions SSL]** ![Interfaz de usuario gráfica, Texto, Aplicación Descripción generada automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/percona%2Bssl.png)


***

**CONFIGURACIÓ DEL SERVIDOR PERCONA SERVER PER REALITZAR CONNEXIONS
SEGURES SoBRE SSL.**

**1. Comprova mitjançant el programari WireShark que la connexió
d\'autenticació no és segura.**

En primer lloc hem de visualitzar l'estat del Firewall del nostre RedHat, amb l'status!!

![Texto Descripción generada automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image60.png)

Com hem vist prèviament estava activat, procedim amb la desactivació del
firewall:

![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image61.png)

La primera comanda serveix per parar l'estat del Firewall i la segona
comanda serveix per desactivar-lo directament.

Tornem a veure l'estat del nostre Firewall ara.Tal com es veu en la imatge el nostre Firewall ja està desactivat! 

![Texto Descripción generada automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image62.png)

En el nostra servidor creem l'usuari root que pugi connectar-se des de qualsevol màquina amb l\'ordre:

![Texto Descripción generada automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image63.png)

Els permisos són accions que l\'usuari ha de tenir per poder realitzar
accions a la base de dades, i és per això que amb l'usuari root li donem
tot tipus de privilegis a qualsevol objecte, i que aquest es pugui
connectar-se des de qualsevol màquina.

![Texto Descripción generada automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image64.png)

Una vegada fet el pas previ entrem al workbench i creem una conexion amb
mysql i per defecte bé connectada amb SSL.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image65.png)

Per que el wireshark pugui capturar el protocol MYSQL i veure les
sentències i el nom de l\'usuari, hem de desactivar el SSL que ve
connectat per defecte a if available i posar-o a "**No**".

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image66.png)

Ara anem al wireshark i capturem el username. (username=root)

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image67.png)

Fem el mateix que abans però aquesta vegada capturem sentències mysql.Entrem dins de el workbench i fem una sentencia mysql.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image68.png)

Ara que ja hem fet la sentencia mirem que en el wireshark ho captura. Tal com es veu està la sentencia mysql que hem fet.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image69.png)


**2. Indica els passos que has realitzat per configurar el servidor i
fer que un dels usuaris de MySQL es connection mitjançant SSL.**

Modifiquem l'usuari root amb la comanda "**ALTER**",però aquesta vegada li afegim que aquest requereixi SSL.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image70.png)

Ara hem d\'utilitzar el programa ''**WinSCP'',** per tal de copiar els
arxius ***SSL KEY FILE (**arxius amb clau SSL**)***, ***SSL CERT FILE
(**arxius amb certificat SSL**)***, ***SSL CA FILE (**arxius de
certificat autoritari SSL**) ***i que tots aquests estiguin en format
públic.

Hem d'iniciar sessió i donar-li a conectar:

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image71.png)

En el servidor de red-hat, ens dirigim a la ruta **/var/lib/mysql**,seleccionem els arxius que necessitem per el workbench

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image72.png)

Els arrosseguem a la màquina local

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image73-75.png)

Posem la ruta dels tres arxius, en el seu lloc corresponen i tal com es veu, no ens dona cap problema, el contrari, ens mostra que s'ha fet
correctament

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image76.png)

Ara anem al wireshark per comprovar que tot està encriptat i com estem veient el usuari i les sentències mysql estan encriptades.

![](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/image77.png)
