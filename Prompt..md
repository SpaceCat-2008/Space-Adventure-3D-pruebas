# PROYECTO: Juego 3D en navegador (JavaScript + Three.js, autocontenido)

Necesito que generes un proyecto completo de videojuego 3D que funcione directamente en navegador web, sin dependencias externas en tiempo de ejecución (todo debe poder ejecutarse localmente).

## REGLAS GENERALES

- El proyecto debe funcionar completamente offline
- No usar CDNs
- Usar módulos ES6 (`type="module"`)
- Código limpio, estructurado y comentado
- Separar lógica en múltiples archivos JS
- Mantener rendimiento compatible con PC de gama media
- No omitir ningún requerimiento
- No dejar decisiones abiertas
- Entregar TODOS los archivos completos (no fragmentos)

---

# TECNOLOGÍA

Usar Three.js en formato local:

Ruta esperada:

/proyecto-juego/
│
├── index.html
├── /libs/
│ └── three.module.js
│
├── /js/
│ ├── main.js
│ ├── game.js
│ ├── player.js
│ ├── enemy.js
│ ├── bullet.js
│ ├── level.js
│ ├── ui.js
│ ├── audio.js
│ └── utils.js
│
├── /assets/
│ ├── sounds/
│ │ ├── shoot.wav
│ │ ├── explosion.wav
│ │ └── bg.mp3
---


---

# CONCEPTO DEL JUEGO

Juego 3D estilo lateral (tipo Super Mario World) con scroll continuo.

- Ambientación: lunar
- Jugador: astronauta con jetpack
- Enemigos: gatos extraterrestres
- Objetivo: avanzar niveles y recolectar partes de nave

---

# CONTROLES

- W → mover derecha
- A → mover izquierda
- S → bajar (cuando aplique)
- D → subir (cuando aplique)
- ESPACIO → salto
- ESPACIO sostenido → jetpack (máx 2 segundos)
- CLICK IZQUIERDO → disparo
- MOUSE → apuntar libremente (crosshair centrado en cursor)

---

# JUGADOR

Características:

- Vida máxima: 100
- No regeneración automática
- Solo se recupera con corazones

Jetpack:
- Duración máxima: 2 segundos
- Se recarga completamente en 2 segundos

Disparo:
- Proyectil visible (NO hitscan)
- Disparo por clic individual (no automático)
- Velocidad alta pero visible

---

# DAÑO DEL JUGADOR

- Enemigo pequeño → 10 daño
- Enemigo mediano → 15 daño
- Enemigo grande/jefe → 20 daño

---

# SISTEMA DE VIDA

- Barra de vida visible (HUD)
- Corazones:
  - Pequeño: +15
  - Mediano: +25
  - Grande: +40

- La vida se mantiene entre niveles
- Los corazones no recogidos pueden recolectarse luego (no reaparecen)

---

# ENEMIGOS

Tipos:

1. Pequeño → 80 HP
2. Mediano → 120 HP
3. Grande → 180 HP

Características:

- Se mueven hacia el jugador
- Disparan con ligera imprecisión
- También causan daño por contacto
- Tienen barra de vida visible

---

# JEFES

- Uno por nivel
- Vida:
  - Nivel 1: 200 HP
  - Escala progresivamente hasta 500 HP en nivel 5

Habilidades:
- Disparo
- Mayor velocidad
- Mayor tamaño

---

# NIVELES

- Total: 5
- Scroll lateral continuo
- Spawn progresivo de enemigos
- Dificultad progresiva:
  - Nivel 1: 10%
  - Nivel 5: 80%

Al completar:
- Se obtiene una parte de nave
- Se muestra en HUD

---

# ESCENARIO

Elementos:

- Terreno lunar
- Rocas (obstáculos)
- Plataformas móviles:
  - Movimiento vertical constante
  - Suben y bajan continuamente

---

# SPAWN

- Enemigos aparecen progresivamente
- Máximo controlado en pantalla
- Cuando se eliminan todos:
  - NO aparecen más
  - Se permite volver atrás a recoger recursos

---

# COMBATE Y EFECTOS

- Disparo láser visible
- Impactos:
  - Destello al recibir daño
  - Explosión al morir enemigo

---

# CÁMARA

- Vista lateral tipo Super Mario World
- Seguimiento suave del jugador
- Movimiento natural

---

# UI (HUD)

Debe mostrar:

- Barra de vida
- Nivel actual (1 a 5)
- Contador de partes de nave
- Mira (crosshair en cursor)

---

# PANTALLA INICIAL

Debe incluir:

- Instrucciones completas
- Botón "Jugar" centrado

---

# AUDIO

- Música de fondo (loop)
- Sonidos:
  - Disparo
  - Explosión
- Botón para activar/desactivar audio

---

# MUERTE DEL JUGADOR

- Reinicia en el mismo nivel
- Vida vuelve a 100
- No reinicia progreso global

---

# GUARDADO

- NO guardar progreso
- Reinicio completo al cerrar navegador

---

# IMPLEMENTACIÓN TÉCNICA

- Usar clases ES6
- Separar responsabilidades por archivo
- Sistema de loop con `requestAnimationFrame`
- Manejo de colisiones básico pero funcional
- Optimizar rendimiento (no crear objetos innecesarios)

---

# SCRIPT INICIAL DE ESTRUCTURA

Genera además un script (Node.js o bash) que cree automáticamente la estructura de carpetas:

Ejemplo esperado:

```bash
mkdir -p proyecto-juego/libs
mkdir -p proyecto-juego/js
mkdir -p proyecto-juego/assets/sounds

touch proyecto-juego/index.html

touch proyecto-juego/js/main.js
touch proyecto-juego/js/game.js
touch proyecto-juego/js/player.js
touch proyecto-juego/js/enemy.js
touch proyecto-juego/js/bullet.js
touch proyecto-juego/js/level.js
touch proyecto-juego/js/ui.js
touch proyecto-juego/js/audio.js
touch proyecto-juego/js/utils.js
