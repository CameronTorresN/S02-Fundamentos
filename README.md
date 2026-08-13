# S02-Fundamentos

_**GUÍA IA:**_
- Tuve temas con las cosas con frame rate, entonces le pedí a ChatGPT que me ayudara a hacer que la velocidad de seguimiento del cursor se sintiera igual sin importar el FPS. (línea 87, 222 y 52).

- También ChatGPT sugirió fijar mi frame rate a 60, pero yo no quería eso. Luego insistió varias veces en repetir variables pero no le hice caso y solo tomé sus ayudas de velocidad. 

## Qué puse en config y qué dejé fuera a propósito
  Adentro: particleCount, proportions, speedRange, radiusRange, alphaRange, color, bounce, gravity — todo lo que describe cómo se ve y actúa el sistema de " partículas"

Fuera, a propósito:
- bouncingCircle y followerCircle (su speed, radius, smoothing) — el brief pedía específicamente cantidad/tamaños/velocidades/paleta/rebote de partículas. Meter ahí los círculos individuales habría mezclado dos cosas que no comparten forma (no tienen tipos, no cambian por instancia).
  
- width / height — no son configuración Cambian solos en resize().

## Dónde estuve a punto de copiar y pegar
Tres lugares:
- bounce() — la tentación era escribir el check de pared para X y luego pegarlo cambiando x→y, vx→vy (que es exactamente como estaba antes). En vez de eso, la función recibe los nombres de propiedad como strings (bounce(p, 'x', 'vx', width)), y ya sirve para ambos.

- makeParticle() — casi hice makeLightParticle() y makeHeavyParticle() como funciones con los mismos campos y distintos números hardcoded. entonces mejor hice makeParticle(type) que jala sus rangos.

- initParticles() — pude haber escrito "haz 350 ligeras" y "haz 150 pesadas" como dos loops con números fijos. Mejor busqué que calculara counts a partir de proportions, así nunca hay que volver a escribir nada si cambias el porcentaje (Aquí también le pedí a chat un poco de guía de como podríâ hacer esto).
