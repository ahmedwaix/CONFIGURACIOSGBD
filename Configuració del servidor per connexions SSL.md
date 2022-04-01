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

# **[Configuració del servidor per connexions SSL]** ![Interfaz de usuario gráfica, Texto, Aplicación Descripción generada     automáticamente](https://github.com/ahmedwaix/CONFIGURACIOSGBD/blob/main/imagenes/percona%2Bssl.png)


***

**CONFIGURACIÓ DEL SERVIDOR PERCONA SERVER PER REALITZAR CONNEXIONS
SEGURES SoBRE SSL.**

**1. Comprova mitjançant el programari WireShark que la connexió
d\'autenticació no és segura.**

En primer lloc hem de visualitzar l'estat del Firewall del nostre Red
Hat, amb l'status!![Texto Descripción generada
automáticamente](./images//media/image1.png)

Com hem vist prèviament estava activat, procedim amb la desactivació del
firewall:

![Texto Descripción generada
automáticamente](./images//media/image2.png)

La primera comanda serveix per parar l'estat del Firewall i la segona
comanda serveix per desactivar-lo directament.

Tornem a veure l'estat del nostre Firewall ara. ![Texto Descripción
generada
automáticamente](./images//media/image3.png)Tal com es veu en la imatge el nostre
Firewall ja està desactivat!

En el nostra servidor creem l'usuari root que pugi connectar-se des de
qualsevol màquina amb l\'ordre:

![Texto Descripción generada
automáticamente](./images//media/image4.png)

Els permisos són accions que l\'usuari ha de tenir per poder realitzar
accions a la base de dades, i és per això que amb l'usuari root li donem
tot tipus de privilegis a qualsevol objecte, i que aquest es pugui
connectar-se des de qualsevol màquina

![Texto Descripción generada
automáticamente](./images//media/image5.png)

Una vegada fet el pas previ entrem al workbench i creem una conexion amb
mysql i per defecte bé connectada amb SSL.

![](./images//media/image6.png)

Per que el wireshark pugui capturar el protocol MYSQL i veure les
sentències i el nom de l\'usuari, hem de desactivar el SSL que ve
connectat per defecte a if available i posar-o a
"**No**".![](./images//media/image7.png)

Ara anem al wireshark i capturem el username. (username=root)

![](./images//media/image8.png)

Fem el mateix que abans però aquesta vegada capturem sentències mysql.
Entrem dins de el workbench i fem una sentencia
mysql.![](./images//media/image9.png)

![](./images//media/image10.png)Ara que ja hem fet la sentencia mirem que
en el wireshark ho captura. Tal com es veu està la sentencia mysql que
hem fet.

**2. Indica els passos que has realitzat per configurar el servidor i
fer que un dels usuaris de MySQL es connection mitjançant SSL.**

Modifiquem l'usuari root amb la comanda "**ALTER**",però aquesta vegada
li afegim que aquest requereixi
SSL.![](./images//media/image11.png)

Ara hem d\'utilitzar el programa ''**WinSCP'',** per tal de copiar els
arxius ***SSL KEY FILE (**arxius amb clau SSL**)***, ***SSL CERT FILE
(**arxius amb certificat SSL**)***, ***SSL CA FILE (**arxius de
certificat autoritari SSL**) ***i que tots aquests estiguin en format
públic.

Hem d'iniciar sessió i donar-li a conectar:

![](./images//media/image12.png)

En el servidor de red-hat, ens dirigim a la ruta **/var/lib/mysql**,
seleccionem els arxius que necessitem per el workbench

![](./images//media/image13.png)

Els arrosseguem a la màquina local

![](./images//media/image14.png)![](./images//media/image15.png)![](./images//media/image16.png)

Posem la ruta dels tres arxius, en el seu lloc corresponen i tal com es
veu, no ens dona cap problema, el contrari, ens mostra que s'ha fet
correctament![](./images//media/image17.png)

Ara anem al wireshark per comprovar que tot està encriptat i com estem
veient el usuari i les sentències mysql estan encriptades.

![](./images//media/image18.png)
