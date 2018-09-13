# Sistemas-Operativos
Este repositorio contara con las practicas que veremos en clase de Sistemas Operativos, es pùblico para que el profesor y otros compañeros puedan revisarlo y conmplementarlo

/*
  Programa para un par de semaforos que cambian de uno
  a otro, y la implementacin de un boton para terminar
  el tiempo de la luz verde y pasar al otro.
*/
// Declaramos la variable para el pin del boton
const int button = 8;

void setup() {
  // Con un ciclo activamos los pines del 2 al 7 como salidas
  for (int pin = 2; pin <= 7; pin++) {
    pinMode(pin, OUTPUT);
  }
  // El pin del boton lo ponemos como entrada
  pinMode(button, INPUT);
}

// Funcion para el primer semaforo y sus cambios de estado
void semaphoreOne() {
  digitalWrite(2, HIGH);
  int count = 0;
  while (count < 30) {
    // El ciclo esta en espera mientras el boton no es presionado
    if (digitalRead(button) == true) {
      break;
    }
    count++;
    delay(200);
  }
  digitalWrite(2, LOW);
  delay(500);
  digitalWrite(2, HIGH);
  delay(500);
  digitalWrite(2, LOW);
  delay(500);
  digitalWrite(2, HIGH);
  delay(500);
  digitalWrite(2, LOW);
  delay(500);
  digitalWrite(2, HIGH);
  delay(500);
  digitalWrite(2, LOW);
  delay(500);
  digitalWrite(2, HIGH);
  delay(500);
  digitalWrite(2, LOW);
  digitalWrite(3, HIGH);
  delay(2500);
  digitalWrite(3, LOW);
  digitalWrite(4, HIGH);
  digitalWrite(7, LOW);
  // Mandamos a llamar al otro semaforo
  semaphoreTwo();
}

// Funcion para el segundo semaforo y sus cambios de estado
void semaphoreTwo() {
  digitalWrite(5, HIGH);
  int count = 0;
  while (count < 30) {
    if (digitalRead(button) == true) {
      break;
    }
    count++;
    delay(200);
  }
  digitalWrite(5, LOW);
  delay(500);
  digitalWrite(5, HIGH);
  delay(500);
  digitalWrite(5, LOW);
  delay(500);
  digitalWrite(5, HIGH);
  delay(500);
  digitalWrite(5, LOW);
  delay(500);
  digitalWrite(5, HIGH);
  delay(500);
  digitalWrite(5, LOW);
  delay(500);
  digitalWrite(5, HIGH);
  delay(500);
  digitalWrite(5, LOW);
  digitalWrite(6, HIGH);
  delay(2500);
  digitalWrite(6, LOW);
  digitalWrite(7, HIGH);
  digitalWrite(4, LOW);
  // Mandamos a llamar al otro semaforo
  semaphoreOne();
}

// Iniciamos nuestro semaforo
void loop() {
  // Cambiamos el estado de todos los leds para
  // que esten apagados todos al inicio
  for (int pin = 2; pin <= 7; pin++) {
    digitalWrite(pin, LOW);
  }
  // Prendemos el verde de un semaforo y el
  // rojo del otro semaforo
  digitalWrite(2, HIGH);
  digitalWrite(7, HIGH);
  // Iniciamos el primer semaforo
  semaphoreOne();
}
