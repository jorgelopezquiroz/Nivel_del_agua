# Practica ESP32 con HC-SR04 Ultrasonic Distance Sensor para saber el nivel de un deposito
En este repositorio muestra como podemos programar una ESP32 con el sensor ultrasonico y LED'S para medir el nivel de agua de un tanque.

## Introducción

### Descripción

La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```HC-SR04 Ultrasonic Distance Sensor```) para adquirir distancia; Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/).


## Material Necesario

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/) como simulador.
- Tarjeta ```ESP 32```.
- Sensor ```HC-SR04 Ultrasonic Distance Sensor```.

- ```LED```



## Instrucciones

### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/), si deseas guardar tu programacion es necesario crear una cuenta en [WOKWI](https://https://wokwi.com/).


### Instrucciones de preparación de entorno 

1. Entramos al simulador [WOKWI](https://https://wokwi.com/) y selecionamos la tarjeta ```ESP 32``` como se muestra en la siguiente imagen.

![](https://raw.githubusercontent.com/jorgelopezquiroz/Nivel_del_agua/7c414a24b9f29c341c4338fd90fb97659d0df407/ESP32.png)



2. Posteriormente se abrirá la terminal de programación y se coloca la siguente programación:

```
// defines pins numbers
const int trigPin = 4;
const int echoPin = 15;
const int led1 = 22;
const int led2 = 21;
const int led3 = 19;
const int led4 = 18;

// defines variables
long duration;
int distance;
int safetyDistance;


void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
pinMode(led4, OUTPUT);
Serial.begin(9600); // Starts the serial communication
}


void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);

// Calculating the distance
distance= duration*0.034/2;

safetyDistance = distance;
if (safetyDistance>=2 && safetyDistance<=40)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=40 && safetyDistance<=80) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if( safetyDistance>=80 && safetyDistance<=120) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, LOW);
}
else if( safetyDistance>=120 && safetyDistance<=160) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, HIGH);
}
else
{
 digitalWrite(led1,  LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}

// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
delay (2000);
}
```
3. No es nesesario instalar ninguna libreria.
 
4. Hacer la conexion de **HC-SR04 Ultrasonic Distance Sensor** con la **ESP32** y **LED'S**  como se muestra en la siguente imagen.

![](https://github.com/jorgelopezquiroz/Nivel_del_agua/blob/main/conexion.png?raw=true)

### Instrucciónes de operación

1. Iniciar la simulación.
2. Visualizar los datos en el monitor serial.
3. Colocar la distancia se da *doble click* al sensor **HC-SR04 Ultrasonic Distance Sensor** para cambiar la distancia.

## Resultados

Cuando haya compilado, verás los valores dentro del monitor serial como se muestra en la siguentes imagenes.
En nuestra programación conforme se esta llenado el tanque se van activando los LED'S cuando este lleno por llenarse el tanque se activaran los 4 LED'S y se apagaran cuando este lleno el tanque.

**INICIO DE LLENADO DEL TANQUE**

***0 a 1/4 DE LLENADO DEL TANQUE***
![](https://github.com/jorgelopezquiroz/Nivel_del_agua/blob/main/INICIO.png?raw=true)

***1/4 a 1/2 DE LLENADO DEL TANQUE***

![](https://github.com/jorgelopezquiroz/Nivel_del_agua/blob/main/1:4.png?raw=true)
***1/2 a 3/4 DE LLENADO DEL TANQUE***

![](https://github.com/jorgelopezquiroz/Nivel_del_agua/blob/main/1:2.png?raw=true)

***3/4 a TANQUE LLENO***
![](https://github.com/jorgelopezquiroz/Nivel_del_agua/blob/main/3:4.png?raw=true)

***TANQUE LLENO***

![](https://github.com/jorgelopezquiroz/Nivel_del_agua/blob/main/FULL.png?raw=true)

## Evidencias
![](https://github.com/jorgelopezquiroz/Nivel_del_agua/blob/main/Evidencia%201.png?raw=true)


![](https://github.com/jorgelopezquiroz/Nivel_del_agua/blob/main/Evidencia%202.png?raw=true)

![](https://github.com/jorgelopezquiroz/Nivel_del_agua/blob/main/Evidencia%203.png?raw=true)

# Créditos

Desarrollado por Jorge Esteban Lopez Quiroz

- [GitHub](https://github.com/jorgelopezquiroz)