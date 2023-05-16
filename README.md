
# TP SPD
![TP-SPD.png](https://github.com/NicoBrites/EjemploDocumentacion/blob/main/img/ArduinoTinkercad.jpg?raw=true "TP SPD") 

## Integrantes

* Nicolas Brites

## Proyecto : Estacion de Subtes

![TP-SPD.png](https://github.com/NicoBrites/TP-SPD/blob/main/img/IMAGEN%20TINKER%20GITHUB.png?raw=true)

## Descripcion
Es un programa simple que simula un subte pasando por las diferentes estaciones ( Constitucion, Independencia, San Juan y Moreno) 
Donde en cada estacion se prende un led y se emite un sonido cada ves que el "subte" llega a una estacion.

## Funciones principales
La funcion prender_led() se encarga de prender los leds dependiendo la estacion que se encuentre


```
void prender_led(int estacion)
{
  if (estacion == 0){
    
    digitalWrite(LED_ROJO_CONSTI, HIGH);
    digitalWrite(LED_AMARILLO_MORENO, LOW);
   
  }else if (estacion == 1){
     digitalWrite(LED_ROJO_CONSTI, LOW);
     digitalWrite(LED_AMARILLO_SANJUAN, HIGH);
    
  }else if (estacion == 2){
     digitalWrite(LED_AMARILLO_SANJUAN, LOW);
     digitalWrite(LED_AMARILLO_INDEPENDENCIA, HIGH);
    
   }else if (estacion == 3){
     digitalWrite(LED_AMARILLO_INDEPENDENCIA, LOW);
     digitalWrite(LED_AMARILLO_MORENO, HIGH);
  }
}
```
La funcion sonar_buzer hace sonar los buzer 

```
void sonar_buzer()
{
   	tone(piezoPin, 1000, 200);
    delay(100);
    noTone(piezoPin);
}
```
Y la funcion imprir_numero() prende el visualizador del 7 segmentos dependiendo de la estacion en la que este 

```

void imprimir_numero(int numero_impreso)
{
  if (numero_impreso == 1)
  {
  digitalWrite(A, LOW);
  digitalWrite(B, HIGH);
  digitalWrite(C, HIGH);
  digitalWrite(D, LOW);
  digitalWrite(E, LOW);
  digitalWrite(F, LOW);
  digitalWrite(G, LOW);

  }
 else if (numero_impreso == 2)
{
  digitalWrite(C, LOW);
  digitalWrite(A, HIGH);
  digitalWrite(B, HIGH);
  digitalWrite(G, HIGH);
  digitalWrite(E, HIGH);
  digitalWrite(D, HIGH);
  digitalWrite(F, LOW);

}
else if (numero_impreso == 3)
{
  digitalWrite(A, HIGH);
  digitalWrite(B, HIGH);
  digitalWrite(C, HIGH);
  digitalWrite(D, HIGH);
  digitalWrite(E, LOW);
  digitalWrite(F, LOW); 
  digitalWrite(G, HIGH);

}

else if (numero_impreso == 0)
{
  digitalWrite(A, HIGH);
  digitalWrite(B, HIGH);
  digitalWrite(C, HIGH);
  digitalWrite(D, HIGH);
  digitalWrite(E, HIGH);
  digitalWrite(F, HIGH);
  digitalWrite(G, LOW);
}
}
```
Y este seria el loop()

```
void loop()
{
   switchState = digitalRead(switchPin); // lee el estado del interruptor

  if (guardar_estado == 1){
    contador =0;}
  
  if (switchState == HIGH) { 
    guardar_estado = 0;
    
   if (contador == 0){
     prender_led(contador);
     imprimir_numero(3);
     sonar_buzer();
     delay(1000);
     contador ++;
    	}
    else if (contador == 1) {
     prender_led(contador);
     imprimir_numero(2);
     sonar_buzer();
     delay(1000);
     contador ++;
    }
   else if (contador == 2) {
    prender_led(contador);
    imprimir_numero(1);
  	sonar_buzer();
    delay(1000);
    contador ++;
    }
    else if (contador == 3) {
     prender_led(contador);
     imprimir_numero(0);
     sonar_buzer();
     delay(1000);
     contador = 0;
    }
    }
   
   else if (switchState == LOW) { // si el interruptor está apagado 
	
      digitalWrite(LED_ROJO_CONSTI, LOW);
      digitalWrite(LED_AMARILLO_SANJUAN, LOW);
      digitalWrite(LED_AMARILLO_INDEPENDENCIA, LOW);
      digitalWrite(LED_AMARILLO_MORENO, LOW);
    
      digitalWrite(A, LOW);
      digitalWrite(B, LOW);
      digitalWrite(C, LOW);
      digitalWrite(D, LOW);
      digitalWrite(E, LOW);
      digitalWrite(F, LOW);
      digitalWrite(G, LOW);
    
      contador == 0;
      guardar_estado = 1;
  }
```
## Link al proyecto

[Proyecto en tinkerkad](https://www.tinkercad.com/things/jS1DVyVxO4A?sharecode=nAp98lj0n092F84sj0OGpgIMbh7YLPH5a8tqHJ1LTE8)




