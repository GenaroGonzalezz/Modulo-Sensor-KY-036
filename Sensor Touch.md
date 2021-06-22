# MÓDULO SENSOR TACTIL METALICO KY-036

## Descripción General
<p> 
El módulo sensor táctil metálico KY-036 tiene 3 componentes principales en su placa de circuito. Primero, la unidad de sensor en la parte frontal del módulo que mide el área físicamente y envía una señal analógica a la segunda unidad, el amplificador. El amplificador amplifica la señal, según el valor de resistencia del potenciómetro, y envía la señal a la salida analógica del módulo.
El tercer componente es un comparador que cambia la salida digital y el LED si la señal cae por debajo de un valor específico.
</p>
<div style="text-align:right"><img src="https://sensorkit.en.joy-it.net/images/9/9f/ky-036.jpg" /></div>

## Especificaciones
<p>
  Emite una señal si se tocó la pica de metal del sensor. Puede ajustar la sensibilidad del sensor con el controlador.

Salida digital:  en el momento de la detección del contacto, se emitirá una señal. 

Salida analógica:  valor de medición directo de la unidad de sensor.
</p>


![Imagen](https://sensorkit.en.joy-it.net/images/d/d8/4_dig_V_G_An_eng.png)

## Desarrollo de la práctica
<p>
Se llevó a cabo la conexión del sensor Reed Switch en conjunto con un display LCD de manera que se pueda conocer el estado actual del componente al interactuar con un elemento que posea propiedades magnéticas, interactuando así con el circuito y alterando su comportamiento el cual se presenta en pantalla por medio de un mensaje de cambios.
</p>



 ### Conexión

KY-025	| Arduino
--------|-------
A0 |	40
G	| GND
" +	"| 5V
D0 | D0



<p>
A continuación se puede observar el circuito completo en el cual se encuentra conectado el módulo al Arduino, así como también se aprecia el imán que será utilizado para llevar a cabo las pruebas.
</p>

![Pruebas1](https://github.com/GenaroGonzalezz/Modulo-sensor-KY-025/blob/main/200281094_4189357484453623_5645018992284595790_n.jpg)

## Imagen 1

![Pruebas2](https://github.com/GenaroGonzalezz/Modulo-sensor-KY-025/blob/main/200087686_160587269438462_2896078833731179641_n.jpg)

## Imagen 2
<p>
En la siguiente imagen es posible observar el cambio de estado del módulo durante su interacción con el imán.
</p>

![Pruebas3](https://github.com/GenaroGonzalezz/Modulo-sensor-KY-025/blob/main/202780707_242333810600301_9135937306506871131_n.jpg)

## Código
```
//========================LIBRERIAS==================
#include "Arduino.h"
#include <LiquidCrystal.h>
#include <Servo.h>

//================sensores======================
int sensor = 40;
int lectura;
//========================LCD config====================================

LiquidCrystal lcd(8, 9, 4, 5, 6, 7);

void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  lcd.begin(16,2);
  pinMode(sensor,INPUT);
  
}

void loop() {
  

  lectura = digitalRead(sensor);
  Serial.println(lectura);

  if (lectura == LOW)
    {
    lcd.clear();
    lcd.setCursor(0,0);
    lcd.print("Deteccion toque:");
    lcd.setCursor(1,1);
    lcd.print("Positiva");
    }
   else
  {
    lcd.clear();
    lcd.setCursor(0,0);
    lcd.print("Deteccion toque:");
    lcd.setCursor(1,1);
    lcd.print("Negativa");
    }
  
  delay(200);
}
```
