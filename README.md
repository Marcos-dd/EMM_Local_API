# EMM_Local_API
Programa automatizado de extracción y representación de datos alojados en la web del Banco de España.

## Extract, Move & Merge - EMM Local API  (Beta Version) - V.2.7
-----------------------------------------------------

EMM es un **programa de extracción de datos automatizado**. Dicha extracción la realiza desde la página web del banco de españa *http://app.bde.es/rss_www/* , desde donde se descargarán todos los archivos excel solicitados de todos los ejercicios disponibles en la web (actualmente del 2000 al 2020).

EMM crea **una gráfica por sector** donde se muestra la **evolución de los ratios sectoriales** R16 (Cifra Neta de Negocio / Total Activo) y R10 (Resultado Económico Neto / Total Activo), **otra gráfica por sector** donde se muestra la **evolución del número de empresas** sujetas al estudio y **una última gráfica comparativa conjunta de las tasas de variación media de R16 y R10 (TVM)**.

*Dichos ratios pueden ofrecer una simplificación suficiente para entender la evolución de los sectores y el impacto de las crisis sobre ellos.*

-----------------------------------------------------
### CARACTERÍSITCAS DE LA VERSIÓN 2.7
En esta versión Beta se estudian el ratio **R16**, que se muestra como **Rentabilidad** y el **R10** , que se muestra como **Rendimiento**.   

Los **sectores predefinidos** en esta versión son:   

***C26***-> Fabricación de productos informáticos, electrónicos y ópticos   
***J***-> Información y comunicaciones   
***J62***-> Programación, consultoría y otras actividades relacionadas con la informática   
***J631***-> Procesos de datos, hosting y actividades relacionadas; portales web   
***N***-> Servicios administrativos y auxiliares   
***P***-> Educación   
***Q***-> Sanidad y Servicios Sociales   
***I***-> Hostelería    
  
*En posteriores versiones se podrán seleccionar todos los sectores sobre los que se quiera realizar el estudio.*   

**Países incluidos** en la muestra:   
  
- España  
	
*En posteriores versiones se podrán seleccionar otros países de Europa.*

-----------------------------------------------------
### Antes de ejecutar el programa
Cargue el archivo requirements.txt en su entorno virtual:

pip install -r requirements.txt 

-----------------------------------------------------
### Cómo ejecutar EMM   
1.- Guardar el archivo main.py y funciones.py en local.   
2.- Configurar el path de descargas del navegador a la carpeta de descargas en local (Download por defecto).   
3.- Ejecutar el archivo main.py   

------------------------------------------------------
Una vez ejecutado, el programa se conectará a la web mencionada al inicio, seleccionará los valores predefinidos para las listas desplegables de la página, descargará los excel en *Descargas* y creará dos carpetas, 'data' y 'graficas', en la carpeta local donde se hayan guardado los archivos .py       

En /data creará tantas subcarpetas como sectores se hayan escogido para el estudio.    
Cada subcarpeta llevará el nombre del sector y contendrá los informes del 2000 al 2020 con todos los ratios sectoriales e información complementaria de dicho sector.   
Además creará tres archivos más:   
	- {sector}/enterprises.xlsx: Muestra el número de empresas del sector sometidas al estudio en cada año.        
	Las cifras se obtienen a partir del R16 ya que posee los valores máximos (nº de empresas) en todos los informes, siendo por tanto el ratio más representativo.    
	- {sector}/median.xlsx: Ofrece una muestra de todos los valores Q2 de todos los ratios por cada año.    
	- {sector}/total.xlsx: Tabla resumen que muestra el número de empresas y los ratios sometidos a estudio por cada año.   

En /graficas se crearán, en formato .html, los gráficos interactivos correspondientes a los excel comentados para cada sector así como dos gráficos (TVM.html y TVM_rendimiento.html) donde se mostrarán las correspodientes tasas de variación media de estos 20 años para cada sector.
