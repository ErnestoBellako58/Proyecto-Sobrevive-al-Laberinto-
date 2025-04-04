# 🔥🕵️ Sobrevive en el Laberinto

### Proyecto para la materia de **Programación Concurrente**  
**Lenguaje:** Python  
**Equipo:**
- Ricardo Medina Carrillo  
- Lara Estévez Santiago  
- Rojas Pérez Ernesto  
- José Ángel Avilés Reyes  

---

## 🎯 Objetivo del Proyecto

Desarrollar un videojuego cooperativo en el que varios jugadores deben escapar de un laberinto lleno de trampas y enemigos controlados por inteligencia artificial. Se hace uso de **concurrencia** para permitir que múltiples jugadores y enemigos interactúen de forma simultánea y segura dentro del entorno compartido.

---

## ⚙️ Requerimientos Técnicos

- **Python 3.11+**
- Librerías estándar:
  - `threading`
  - `time`
  - `random`
- Opcional para gráficos: `pygame`
- Sistema Operativo: Windows, Linux o MacOS

---

## 📋 Historias de Usuario (User Stories)

- ✅ Como jugador, quiero moverme por el laberinto en tiempo real.
- ✅ Como jugador, quiero colaborar con otros jugadores para poder escapar más rápido.
- ✅ Como jugador, quiero evitar trampas colocadas en el laberinto.
- ✅ Como enemigo (IA), quiero patrullar de forma autónoma y atacar si detecto jugadores cerca.
- ✅ Como sistema, quiero evitar que dos hilos modifiquen el mapa al mismo tiempo para evitar inconsistencias.

---

## 🔧 Funcionalidades Priorizadas

| Prioridad     | Funcionalidad                                           |
|---------------|----------------------------------------------------------|
| Must-have     | Hilos por jugador con candado para acceder al mapa       |
| Must-have     | Enemigos simulados con IA en hilos separados             |
| Must-have     | Uso de `Lock` para prevenir condiciones de carrera       |
| Nice-to-have  | Uso de `asyncio` para tareas no críticas                 |
| Nice-to-have  | Balance automático de dificultad según progreso del juego|

---

## 🧩 Diseño Técnico

### Diagrama de Flujo

```mermaid
graph TD
    Start --> InitPlayers
    InitPlayers --> |Thread por jugador| PlayerThread1
    InitPlayers --> PlayerThread2
    InitPlayers --> EnemyThread
    PlayerThread1 --> Mapa
    PlayerThread2 --> Mapa
    EnemyThread --> Mapa
    Mapa --> Verificación{¿Colisión o evento?}
    Verificación --> Fin
