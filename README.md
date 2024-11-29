# SolaxPower-SK-SU5000E
|Solax Power |SK-SU5000E|
|------------|---------------|
|![Logo_SolaxPower](https://user-images.githubusercontent.com/19588354/131035030-72bfaffb-bd52-41cd-9cf3-d621af49c739.png) | ![SolaX-X-Hybrid-Inverter-removebg-preview](https://user-images.githubusercontent.com/19588354/131035350-7df1f799-357f-4644-8a80-bdbcd8117d63.png) |

Monitorizar nuestro inversor **SolaxPower SK-SU5000E de 4.6kW** con **Grafana e InfluxDB 2.0**, sin depender del portal web oficial.

---

## Introducción

Este modelo de inversor pertenece a la **1ª Generación**, cuya plataforma oficial de monitorización es [www.solax-portal.com](http://www.solax-portal.com).  
La **3ª Generación** utiliza [www.solaxcloud.com](http://www.solaxcloud.com), pero **ambos portales no son compatibles entre sí**.

### Limitaciones de la plataforma oficial:
- **Falta de API:** El portal **solax-portal.com** no ofrece opciones para acceder a los datos mediante API.
- **Tiempo limitado de datos:** Los gráficos están disponibles por un período de **aproximadamente 1 año**.
- **Exportación manual:** Sólo es posible exportar datos en formato Excel (.csv), lo que no es muy visual.

### Solución propuesta:
Con este repositorio aprenderemos a:
1. **Monitorizar el inversor en conexión local**, sin depender del portal oficial.
2. **Utilizar herramientas Open Source** para crear un sistema personalizado y almacenar datos de forma indefinida (dependiendo de los recursos de tu servidor o PC).

---

## Requisitos

### Hardware
- **PC local**, **Servidor NAS** o **Raspberry Pi**  
  *(Dependiendo de tus recursos económicos o disponibles).*

### Software
- **Docker** (compatible con Windows, Linux, Mac o Raspberry Pi).
- **Node-Red** (Docker).
- **InfluxDB 2.0** (Docker).
- **Grafana** *(opcional, ya que InfluxDB también tiene opciones gráficas).*

---

## Pasos para la configuración

### **Paso 1: Configuración de Node-Red**

1. Instalar y acceder a Node-Red desde su portal web.
   - Si no tienes habilitado el usuario **Admin**, es posible acceder sin usuario predeterminado.
   - Para habilitar el usuario **Admin**, edita las configuraciones desde la consola de comandos.

2. En Node-Red, utiliza los bloques necesarios para obtener información del inversor en tu red local.  
   Esta información será traducida y enviada a tu base de datos (**InfluxDB 2.0**) o **MySQL**.  
   *(Recomendación: Usar **InfluxDB 2.0** para este proyecto).*

| **Ejemplo de configuración en Node-Red:** |
|------------------------------------------|
|![SolaxPower_SK-SU5000E_Node-Red](https://user-images.githubusercontent.com/19588354/131035919-14f3c56c-e17e-45f2-b0a8-8d9bc28e4c21.jpg)|

| **Bloques de funciones en Node-Red:** |
|--------------------------------------|
|![SolaxPower_SK-SU5000E_Node-Red_functions](https://user-images.githubusercontent.com/19588354/131037062-941eae52-ec44-4759-b664-f097da05b6e8.jpg)|

#### URLs para obtener datos:

- **Datos en tiempo real:**
```
  Método GET: http://192.168.X.X/api/realTimeData.html
```
- **Datos históricos:**
```
  Método GET: http://192.168.X.X/api/historyData.html
```
- **Datos en tiempo real desde la nube (solax-portal.com):**
```
  Método GET: https://www.solax-portal.com/api/v1/site/overview/123456/?token=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```
- **Datos históricos desde la nube (solax-portal.com):**
```
  Método GET: https://www.solax-portal.com/api/v1/site/inverterlist/123456/?token=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```

---
### **Paso 2: Configuración de InfluxDB 2.0**
1. Asegúrate de que los datos recopilados en Node-Red se envían correctamente a la base de datos.
2. Revisa los datos en InfluxDB con las funciones configuradas.

|**Ejemplo de visualización en InfluxDB:**|
|-----------------------------------------|
|![SolaxPower_SK-SU5000E_InfluxDB2 0](https://user-images.githubusercontent.com/19588354/131036865-e4538fb4-2af7-4902-a2b9-d5d7e140304c.jpg)|

### **Paso 3: Configurar Grafana (opcional)**
1. Integra Grafana con InfluxDB para una monitorización avanzada.
2. Diseña dashboards personalizados para una experiencia visual más rica.

|**Ejemplo de visualización en Grafana:**|
|----------------------------------------|
|![SolaxPower_SK-SU5000E_Grafana](https://user-images.githubusercontent.com/19588354/131038328-0dfb19dc-cdcf-488c-9c2f-502431fa7607.jpg)|

### Vistas avanzadas con Grafana
Utiliza plugins como Flowcharting o Diagrams para crear visualizaciones interactivas de tu hogar o negocio.

> Nota: Diseños avanzados pueden aumentar la carga en el sistema. Optimiza tus recursos para mantener una respuesta rápida.

|**Ejemplo dinámico:**|
|---------------------|
|![VID_20220126_215008_1](https://user-images.githubusercontent.com/19588354/151346870-ed0e3957-e0b6-4342-af19-9858e2490651.gif)|

---

## Curso completo Grafana 8 Principiantes 2022
Aquí podréis encontrar lo esencial y con certificado GRATIS en la plataforma web que fundé con la marca [**GATORU ACADEMY®**](https://www.gatoru.com/course/grafana-8-principiante-2022).

Vídeo de ejemplo:
[YouTube Canal Rubén Gámez Torrijos](https://youtu.be/7VVp85DdpOs?si=t2FNu2gJL4u4jvkq)

## Más información
Consulta este tutorial en video: [Monitorización con Grafana e InfluxDB](https://www.youtube.com/watch?v=9i_naLjdNTw).
