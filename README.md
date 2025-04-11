# 🔥🕵️ Sobrevive en el Laberinto

### Proyecto final para la materia de **Programación Concurrente**  
**Lenguaje:** Python  
**Equipo:**
- Ricardo Medina Carrillo  
- Lara Estévez Santiago  
- Rojas Pérez Ernesto  
- José Ángel Avilés Reyes  

---

## 🎯 Objetivo del Proyecto

Diseñar e implementar un videojuego multijugador cooperativo donde los jugadores deben escapar de un laberinto lleno de trampas y enemigos. El enfoque principal es demostrar el uso de **programación concurrente** mediante hilos y sincronización de recursos, gestionando múltiples interacciones en tiempo real entre jugadores, enemigos y el entorno.

---

## ⚙️ Requerimientos Técnicos

- **Python 3.11+**
- Librerías estándar:
  - `threading`
  - `time`
  - `random`
- Recomendado para interfaz gráfica: `pygame`
- Sistema operativo compatible: Windows, Linux o MacOS

---

## 💡 Implementación Concurrente

- Se utiliza un **hilo por jugador**, cada uno con acceso controlado al mapa compartido mediante mecanismos de sincronización (`Lock`).
- Los **enemigos IA** operan en hilos independientes, patrullando de forma autónoma y reaccionando al entorno.
- El acceso concurrente al laberinto se maneja cuidadosamente para **evitar condiciones de carrera**, inconsistencias visuales y errores de lógica.
- La lógica del juego está dividida en **módulos concurrentes** para facilitar el mantenimiento y la escalabilidad del proyecto.
- En el segundo parcial se trabajó en la **optimización del rendimiento**, agregando monitoreo del uso de CPU y análisis de tiempos de respuesta.

---

## 📋 Historias de Usuario

- ✅ Como jugador, quiero moverme libremente por el laberinto en tiempo real.
- ✅ Como jugador, quiero colaborar con otros jugadores para planear la salida.
- ✅ Como jugador, quiero evitar trampas o enemigos que bloqueen el camino.
- ✅ Como enemigo (IA), quiero detectar jugadores y patrullar con autonomía.
- ✅ Como sistema, quiero asegurar la sincronización al modificar el estado del mapa.

---

## 🔧 Funcionalidades Priorizadas

| Prioridad     | Funcionalidad                                           |
|---------------|----------------------------------------------------------|
| Must-have     | Hilos por jugador con control de acceso sincronizado     |
| Must-have     | Enemigos con lógica IA independiente y concurrente       |
| Must-have     | Uso de `Lock` para evitar conflictos en memoria compartida|
| Should-have   | Estadísticas de rendimiento del sistema (CPU, hilos)     |
| Nice-to-have  | Ajuste automático de dificultad según el avance del jugador|
| Nice-to-have  | Interfaz gráfica simple con `pygame`                     |

---

## 🧠 Arquitectura y Diseño

### Núcleo Concurrente

- El **núcleo del juego** se basa en la lógica concurrente de movimientos, colisiones y eventos, integrando múltiples hilos con sincronización estricta.
- La estructura sigue el principio de **modularidad concurrente**, permitiendo que cada componente (jugador, enemigo, controlador) sea una entidad paralela que se comunica con un mapa central.

### Diagrama de Flujo

```mermaid
graph TD
    Start --> InitGame
    InitGame --> CreateThreads
    CreateThreads --> |Hilo Jugador 1| Player1
    CreateThreads --> |Hilo Jugador 2| Player2
    CreateThreads --> |Hilo Enemigo IA| Enemy1
    Player1 --> Mapa
    Player2 --> Mapa
    Enemy1 --> Mapa
    Mapa --> Evento{¿Colisión / Evento?}
    Evento --> Resolución
    Resolución --> Fin
