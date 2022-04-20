# DAC_ESP32_Speaker
## Un ejemplo de importar audio para reproducirlo utilizando la DAC de la ESP32.
Para poner en funcionamiento la DAC ESP32 WROOM primero debemos tener en cuenta su conexión que se conectara a la primera DAC1 como se indica en la figura y la demás conexión a GND Y 5V
 ![img1](https://github.com/ArtilRobotics/DAC_ESP32_Speaker/blob/4dc30972ec01c0e0e45e3fdf93d6f8719e2c07a9/Imagenes/1%20configuracion%20de%20conexion.png)
Para poder reproducir una música por la DAC primero se debe exportar la música en binario con el uso de un programa que vera a continuación:
Para poder descargar el programa se deberá dirigir al siguiente link: https://mh-nexus.de/en/hxd/
![img2](https://github.com/ArtilRobotics/DAC_ESP32_Speaker/blob/4dc30972ec01c0e0e45e3fdf93d6f8719e2c07a9/Imagenes/2%20importar%20audio.png)
 
El programa se llama HxD y procedemos a abrir la música que queremos convertir hay que tener en cuenta que la ESP_32 tiene memoria limitada asi que solo exportaremos unos 5 segundos de la música
 ![img3](https://github.com/ArtilRobotics/DAC_ESP32_Speaker/blob/4dc30972ec01c0e0e45e3fdf93d6f8719e2c07a9/Imagenes/3%20convertir%20audio%20a%20bits.png)
Se selecciona todos los archivos generados y se los copia como archivo C

Una vez copiado se pegará al inicio de la programación ino pero que hay que tener en cuenta que siempre cambiará la cantidad de archivos generados como se encuentra por consiguiente.
``` unsigned char rawData[68950]={ ```
 
Ese número deberá ser copiado y ser pegado en esta parte de la programación 
 ``` void loop() { ```
 ``` for (int i=0; i<68950; ++i){ ```
Y se ejecutara para ser escuchado 


Para el circuito de amplificador
En este diagrama la salida del DAC1 de la ESP32 será conectada en el potenciómetro y este a su vez en la entrada de ganancia (Gain in) del LM386 tener en cuenta la alimentación del LM386
 ![img4](https://github.com/ArtilRobotics/DAC_ESP32_Speaker/blob/4dc30972ec01c0e0e45e3fdf93d6f8719e2c07a9/Imagenes/4%20conexion%20amplificador.png)
# Investigación de componentes 
## LM2904
 ![img5](https://github.com/ArtilRobotics/DAC_ESP32_Speaker/blob/4dc30972ec01c0e0e45e3fdf93d6f8719e2c07a9/Imagenes/5%20LM2904.png)
**¿Qué es LM2904 IC?**
Un amplificador que tiene alta ganancia, dos independientes y con compensación de frecuencia en el interior se conoce como LM2904 IC. Este IC opera a través de un solo fuente de alimentación con la ayuda de una amplia gama de voltajes. Los circuitos integrados alternativos de este amplificador son MCP602, LM358, NE5532, RC4558, OPA2134, OPA2228 y OPA2604.
**Configuración de pines IC LM2904**
El diagrama de pines del LM2904 IC se muestra a continuación. Cada pin de este amplificador y su funcionalidad se describen a continuación.
Configuración de pines
 ![img6](https://github.com/ArtilRobotics/DAC_ESP32_Speaker/blob/4dc30972ec01c0e0e45e3fdf93d6f8719e2c07a9/Imagenes/6%20pines%20lm2904.jpg)
- Pin 1 (SALIDA A): Este pin es el o / p del op-amp A
- Pin 2 (ENTRADA A): Este pin es la inversión i / p del op-amp A
- Pin 3 (INPUT A +): este pin es el i / p no inversor del amplificador operacional A
- Pin 4 (GND): Este pin es el pin de voltaje de suministro -Ve o el pin GND.
- Pin 5 (INPUT B +): este pin es el pin no inversor del amplificador operacional B
- Pin 6 (ENTRADA B-): Este pin es el pin inversor del amplificador operacional B
- Pin 7 (SALIDA B): Este pin es el o / p del amplificador operacional B
- Pin 8 (VCC): este pin es el suministro de voltaje positivo.
**Características**
*Las principales características de LM2904 IC incluyen las siguientes.* 
- Los suministros de voltaje son una amplia gama
- La corriente de polarización de entrada es baja
- La compensación de frecuencia es interna
- Tanto la tensión de compensación i / p como la corriente de compensación son bajas
- El rango de voltaje diferencial i / p es equivalente al voltaje de la fuente de alimentación
- El rango de entrada de voltaje de modo común incluye principalmente tierra
- Las salidas se pueden proteger contra cortocircuitos
- Compensado internamente
- La gama de modo común se extiende al suministro de -Ve
- La operación de suministro es simple y dividida
- Los paquetes disponibles no contienen plomo
**Aplicaciones**
*Las aplicaciones de LM2904 IC Incluya lo siguiente.*
- Comparadores
- Transductor Amplificadores
- Controlador LED
- Circuitos amplificadores operacionales convencionales
- Fuente de corriente fija
- Integrador
- Amplificador de poder
- Diferenciador
- Disipador de corriente de alta conformidad
- Sumador
- Diferencia Corriente de polarización de entrada del amplificador
- Seguidor de voltaje
- Cancelación de la corriente de polarización de entrada causada por el error
- Multímetros digitales
- Osciloscopios
- Walkie-talkie
- Solución de gestión de baterías
- Amplificadores sumadores
- Multivibradores
- Osciladores
- Bloque de ganancia de CC

# SGM4890

  ![img7](https://github.com/ArtilRobotics/DAC_ESP32_Speaker/blob/4dc30972ec01c0e0e45e3fdf93d6f8719e2c07a9/Imagenes/7%20SGM4890YMS%20.png)
La mayor aplicación del amplificador operacional dual es como elevador de watts para audio se puede encontrar en su datasheet en el siguiente link: 
https://www.digchip.com/datasheets/parts/datasheet/826/SGM4890YMS-pdf.php 

# Diagrama en KIDCAD

 ![img8](https://github.com/ArtilRobotics/DAC_ESP32_Speaker/blob/4dc30972ec01c0e0e45e3fdf93d6f8719e2c07a9/Imagenes/8%20diagrama%20thinkercad.png)
 
