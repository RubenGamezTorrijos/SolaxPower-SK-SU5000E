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

Paso 2: Ahora en InfluxDB 2.0 vamos a comprobar que los datos son recopilados debidamente con las funciones que hemos realizado en el paso anterior en Node-Red. Adjunto imagen de cómo debería aparecer, siempre dependiendo de vuestros datos e información que hayaís añadido en en el apartado de "function"

Paso 3: Por último si deseamos monitorizarlo en Grafana para poder realizar filtros más detallados y gráficos más personalizados os quedará algo parecido como en la imagen siguiente:

