
# PRACTICA 4: SISTEMAS OPERATIVOS EN TIEMPO REAL

## Descripción del Proyecto

Este proyecto tiene como objetivo comprender el funcionamiento de un sistema operativo en tiempo real mediante la creación y ejecución de varias tareas en un microcontrolador ESP32 utilizando Arduino y FreeRTOS. Se realizarán ejercicios prácticos para observar cómo se dividen y gestionan las tareas en el uso de la CPU.

## Introducción

El ESP32 es un chip altamente utilizado para la creación de dispositivos IoT debido a su potencia, versatilidad y facilidad de programación. En este proyecto, se explorará el uso de FreeRTOS con ESP32 para ejecutar tareas en ambos núcleos del microcontrolador, optimizando así su rendimiento.

## Requisitos

- Microcontrolador ESP32
- Entorno de desarrollo Arduino IDE
- Conocimientos básicos de programación en C/C++
- FreeRTOS

## Contenido del Proyecto

### 1. Multitarea en ESP32 con Arduino y FreeRTOS

Se abordará la programación de tareas en el ESP32 utilizando FreeRTOS para aprovechar los dos núcleos del microcontrolador. Esto permitirá realizar múltiples operaciones de manera simultánea, mejorando la eficiencia y el rendimiento.

### 2. Creación de Tareas

Se explicará cómo crear funciones que contengan el código a ejecutar y cómo asignar estas funciones a tareas específicas. Ejemplo:

```cpp
const int led1 = 2; // Pin del LED

void setup() {
  pinMode(led1, OUTPUT);
  xTaskCreate(
    toggleLED,    // Función a ejecutar
    "Toggle LED", // Nombre de la tarea
    1000,         // Tamaño del stack
    NULL,         // Parámetro a pasar
    1,            // Prioridad de la tarea
    NULL          // Identificador de la tarea
  );
}

void toggleLED(void * parameter) {
  for(;;) {
    digitalWrite(led1, HIGH);
    vTaskDelay(500 / portTICK_PERIOD_MS);
    digitalWrite(led1, LOW);
    vTaskDelay(500 / portTICK_PERIOD_MS);
  }
}
