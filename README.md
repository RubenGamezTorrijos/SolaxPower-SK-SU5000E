# 
![Logo_SolaxPower](https://user-images.githubusercontent.com/19588354/131035030-72bfaffb-bd52-41cd-9cf3-d621af49c739.png)
SolaxPower-SK-SU5000E
![SolaX-X-Hybrid-Inverter-removebg-preview](https://user-images.githubusercontent.com/19588354/131035350-7df1f799-357f-4644-8a80-bdbcd8117d63.png)

Monitorizar nuestro inversor SolaxPower SK-SU5000E de 4.6kW con Grafana e InfluxDB 2.0 sin depender del portal web oficial.

Este modelo de inversor es de 1ª Generación, y su plataforma web oficial para su monitorización es www.solax-portal.com y la nueva para la 3ª Generación es www.solaxcloud.com.
Claro ambos dispositivos no son compatibles con las plataformas, cada uno corresponde a un portal. Pero en este modelo cómo en el portal web de solax-portal.com no tiene la opción de usar una API, lo que vamos a aprender con este repositorio es a monitorizar nuestro inversor en conexión local, es decir sin depender de la plataforma web oficial y con las herramientas de software OpenSource vamos a poder monitorizar y crear nuestro sistema de monitorización y guardar nuestros datos sin infinidamente, (siempre dependiendo de los recursos de nuestro Servidor o PC, ya que en la plataforma web los gráficos sólo son visibles durante un periodo de tiempo, 1 año aprox. Y sólo podemos exportar los datos en formato excel (.csv) pero claro así no es que sea muy visual que digamos. :D:D:D:D
Bien las herramientas que necesitaremos son las siguientes:
1. Hardware: PC local, Servidor NAS, RaspberryPI 2. (Siempre depende de los recursos tanto económicos o disponisbles que tengan actualmente).
2. Software: Docker (Windows, Linux, Mac o RaspberryPi), Node-Red (Docker), InfluxDB 2.0 (Docker) y Grafana (Grafana es opcional ya que InfluxDB tiene también parámetros gráficos par monitorizar).

Una vez tengamos las herramientas y todo instalado, empezaremos cómo configurar nuestros parámetros para poder obtener los datos del inversor SolaxPower SK-SU5000E.

Paso 1: Usaremos la aplicación isntalada Node-Red y accederemos al portal web para su configuración. Es posible aquellos que tengan Node-Red por defecto no tiene el usuario Admin habilitado y podrás acceder sin usuario. (Esto es posible cambiarlo en configuraciones de Node-Red en la consola de comandos). Bien una vez en Node-Red cogeremos las bloques necesarios para obtener la información de nuestro equipo en la red local de nuestra casa o negocio. Y así poder traducir esos datos en el lenguaje legible para poder enviar los mismos datos a nuestra BBDD InfluxDB 2.0 o bien MySQL dependiendo de vuestra elección. (Recomiendo InfluxDB 2.0 par este repositorio). Os dejo una imagen de cómo quedaría en el ejemplo a continuación:

![SolaxPower_SK-SU5000E_Node-Red](https://user-images.githubusercontent.com/19588354/131035919-14f3c56c-e17e-45f2-b0a8-8d9bc28e4c21.jpg)
![SolaxPower_SK-SU5000E_Node-Red_functions](https://user-images.githubusercontent.com/19588354/131037062-941eae52-ec44-4759-b664-f097da05b6e8.jpg)

URL para la obtención de los datos en tiempo real:
```
Methodo GET: http://192.168.X.X/api/realTimeData.html
```
URL para la obtención de datos históricos:
````
Metodo GET: http://192.168.X.X/api/historyData.html 
````
Paso 2: Ahora en InfluxDB 2.0 vamos a comprobar que los datos son recopilados debidamente con las funciones que hemos realizado en el paso anterior en Node-Red. Adjunto imagen de cómo debería aparecer, siempre dependiendo de vuestros datos e información que hayaís añadido en en el apartado de "function"

![SolaxPower_SK-SU5000E_InfluxDB2 0](https://user-images.githubusercontent.com/19588354/131036865-e4538fb4-2af7-4902-a2b9-d5d7e140304c.jpg)


Paso 3: Por último si deseamos monitorizarlo en Grafana para poder realizar filtros más detallados y gráficos más personalizados os quedará algo parecido como en la imagen siguiente:

![SolaxPower_SK-SU5000E_Grafana](https://user-images.githubusercontent.com/19588354/131038328-0dfb19dc-cdcf-488c-9c2f-502431fa7607.jpg)

Ver en más información en YouTube: https://www.youtube.com/watch?v=9i_naLjdNTw

### Crear vistas más realistas de nuestro Hogar o Negocio con Grafana 8.x

> Pueden ver un ejemplo de cómo quedaría una vista personalizada en Grafana gracias un Plugin Flowcharting y uniendo Diagrams podremos hacer cosas incréibles.
> Por supuesto a medida que el archivo JSON que creemos para crear estas imágens dinámicas los recursos de carga se elevan y pueden relentizar la monitorización.
> Es muy importante la optimización del código y recursos del entorno en el que se encuentre, para tener una respuesta inmediata de visualización.
> Muy pronto verán un curso que sacaré explicando todo con más detalles y con diferentes niveles.
> Podrán ver el vídeo de ejemplo en el canal personal: [YouTube Canal Rubén Gámez Torrijos](https://www.youtube.com/watch?v=7VVp85DdpOs).

![VID_20220126_215008_1](https://user-images.githubusercontent.com/19588354/151346870-ed0e3957-e0b6-4342-af19-9858e2490651.gif)

