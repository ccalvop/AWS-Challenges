![AWS_CLI_+_BASH](https://user-images.githubusercontent.com/126183973/223797292-3622deb1-face-47a9-b925-9b27d986cbaa.png)

Lo primero vamos a definir CLI y Bash antes de resolver dos pequeños retos:

**CLI** significa Command Line Interface, que en español se traduce como Interfaz de Línea de Comandos. En el contexto de AWS (Amazon Web Services), CLI es una herramienta que permite interactuar con los servicios de AWS a través de la línea de comandos de un terminal.

**BASH** es una abreviatura de "Bourne-Again SHell", lo que significa que es una versión mejorada del shell original de Unix, llamado "sh" o Bourne shell.
Bash es un shell o intérprete de comandos de Unix y sistemas basados en Unix, como Linux. Shell se refiere a la interfaz de línea de comandos (CLI) que permite a los usuarios interactuar con el sistema operativo a través de comandos de texto. Bash se puede considerar como un lenguaje de scripting, se utiliza principalmente para escribir scripts de shell que automatizan tareas en sistemas basados en Unix.

Los scripts de shell son secuencias de comandos

# **> RETO 1** 

Crear un script utilizando Cloud Shell que muestre cada una de las regiones de AWS junto con sus zonas de disponibilidad asociadas.

**> SOLUCIÓN: _SCRIPT_**

`aws ec2 describe-regions --all-regions --query "Regions[].{Name:RegionName}" --output text | 
xargs -I {} aws ec2 describe-availability-zones --region {} --query "AvailabilityZones[].{Zone:ZoneName, Region:RegionName}" --output table`

1. Solicitamos a aws las regiones mediante el comando **describe-regions** , de todas las regiones con la opción **--all-regions**, 
filtramos la respuesta con la opción **--query** (en este caso solo queremos el nombre de las regiones “**RegionName**”) y con **--output text** 
que la salida sea texto

2. Encadenamos comandos con pipe **|**

3. Usamos el comando **xargs** para utilizar como argumento la salida del primer comando, y con la opción **-I** para reemplazar los valores **{}**

4. Finalmente usamos el comando **describe-availability-zones** con la opción **--region** para ir solicitando las availability zones por cada region. 
Filtraremos los resultados con la opción **--query**, en este caso dos columnas para que se visualice region y sus correspondientes availability zones. 
En este caso la salida conla opción **--output** en tabla para que se visualice de forma más cómoda

5. Se podría añadir la opción **2> /dev/null** para evitar los mensajes de error ocurridos por fallos de autorización.

**_ec2 describe-regions_** - Describes the Regions that are enabled for your account

**_ec2 describe-availability-zones_** - Describes the Availability Zones, Local Zones, and Wavelength Zones that are available to you 

**_xargs_** - Takes in input and executes your chosen command on it

_(*)Guardamos los comandos en un archivo y añadimos una primera línea `#!/bin/bash` para que pueda ser posteriormente ejecutado como un script por bash._

👍**OTRO POSIBLE SCRIPT**

`ec2 describe-regions --all-regions | grep "RegionName" | awk '{print $2}' | tr -d "\"," | 
while read RegionName; do aws ec2 describe-availability-zones --region $RegionName --query
"AvailabilityZones[].{Region:RegionName, Zone:ZoneName}" --output table; done`

En este caso encadenamos con **pipes** diferentes opciones de bash (grep, awk, condicionales para el segundo comando). 
Básicamente con el mismo objetivo, usar los dos comandos **ec2 describe-regions** y **ec2 describe-availability-zones**

:pager: **CAPTURAS DE PANTALLA**

![aws-caso1-ccalvo-p_1-](https://user-images.githubusercontent.com/126183973/223812445-3500bcf0-be39-4e57-8906-9973a000115e.jpg)

![aws-caso1-ccalvo-p_2-](https://user-images.githubusercontent.com/126183973/223812615-5c7e2445-7866-47ea-8e74-18c3265991ba.jpg)

# **> RETO 2** 

Crear un script que muestre el número máximo de instancias EC2 de tipo T que tenemos permitido crear en la región de North Virginia
(AWS Cli permite consultar las “quotas” que tenemos asignadas por cada servicio).

