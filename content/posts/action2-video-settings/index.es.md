---
title: Mis settings de video en la DJI Action 2 para vuelos de proximidad FPV
date: 2026-06-23
draft: false
tags:
  - camara
  - action2
  - ajustes
  - motion blur
  - fpv
summary: "Para capturar la velocidad del vuelo y la belleza del paisaje, quería lograr un motion blur profundo, una exposición equilibrada y un field of view amplio. Para lograrlo, uso dos ajustes clave: ignorar la regla del obturador a 180° y reducir drásticamente la estabilización."
---
Para capturar la velocidad del vuelo y la belleza del paisaje, quería lograr un motion blur profundo, una exposición equilibrada y un field of view amplio. Luego de varias iteraciones, pude lograrlo.

Este post documenta mis settings de video para la DJI Action 2. Encontré dos ajustes clave: ignorar la regla del obturador a 180° y reducir drásticamente la estabilización en Gyroflow.

## Settings base

- **Resolución:** 4K 60fps, formato 4:3.
- **FOV:** Wide (no Ultra Wide). Evito Ultra Wide porque no guarda datos del gyro para la estabilización en Gyroflow.
- **Perfil de color:** D-Cinelike.
- **Balance de blancos:** AWB por ahora (sigo experimentando aquí).
- **Estabilización:** Apagada en cámara. Todo ocurre en Gyroflow.

![Footage RAW](images/motion-blur.gif)

## Exposición en manual

La exposición en Auto es inconsistente y no me daba los resultados que quería para vuelos FPV de proximidad. Como la cámara se mueve constantemente entre cielo brillante y terreno oscuro, los cambios automáticos resultan en imágenes quemadas, zonas oscuras, y muy poco motion blur.

Mis settings actuales son:

- **Velocidad de obturador:** Fija entre 1/60 y 1/80.
- **ISO:** Rango bloqueado entre 100 y 400 (no fijo, no automático completo).
- **Filtros ND:** Indispensables (y elegidos antes de cada vuelo o sesión).

![Action 2 + filtros ND de TBS](images/action2_filter.jpg)

### Test para filtros ND

Antes de cada vuelo o sesión hago una prueba corta:

1. Elijo un filtro ND y configuro la cámara con mis settings base.
2. Apunto al cielo y reviso el nivel de exposición.
3. Apunto al suelo o una superficie oscura y reviso de nuevo.
4. El objetivo: nivel de exposición en 0 o muy cerca en ambos extremos.
5. Si sobreexpone al cielo → ND más oscuro.
6. Si subexpone en las sombras → ND más claro.
7. Si ocurren ambos → ajusto ISO o velocidad de obturador primero, luego repito.

Cuando el nivel de exposición está en 0 (o muy cerca) en ambos extremos, ese es el filtro que uso.

Este ejercicio toma dos minutos y me asegura que no pierda el footage del vuelo completo. Durante la sesión, voy revisando si los settings deben ajustarse por cambios de luz.

## Motion blur profundo

La regla estándar para 60fps es obturador a 1/120 (la regla de los 180°). Para footage convencional seguramente es correcta, pero para FPV no me daba los resultados que esperaba.

A 1/120, el terreno cercano se ve demasiado nítido y detallado. Entre 1/60 y 1/80, obtengo suficiente motion blur para que el terreno en proximidad se vea fluido, sin perder detalle en tomas más lentas o paisajes abiertos.

Ojo, esto solo funciona si la selección de ND es correcta. Un obturador más lento con el ND equivocado quema la imagen. Por eso la prueba previa al vuelo es crítica.

## Una gota de estabilización

Estabilizo en Gyroflow, nunca en la cámara. Pero la lección más importante fue cuánta smoothness aplicar a la estabilización.

Los settings por defecto están en 50% de smoothness, pero para vuelos en proximidad eso es demasiado: se pierde la sensación de movimiento y camufla los reflejos del piloto que son únicos en este tipo de footage. Al probar con otros settings, encontré que un smoothness de 5 y 15% se ajusta mejor a este estilo de vuelo:

- 5%: corrige el wobble más visible. Lo mínimo necesario para filtrar algunas vibraciones del quad sin camuflar el stick input del piloto.
- 15%: un resultado más suave para tomas menos agresivas. Sirve para priorizar paisajes y es más habitual para un público general.

![Settings de Gyroflow al 5% de smoothness](images/gyroflow.png)

**Mis settings actuales:**

| Parámetro            | Valor         |
| -------------------- | ------------- |
| Smoothness           | 5.0% - 15%    |
| Lock horizon         | Off           |
| Dynamic zooming      | On            |
| Zoom limit           | 115%          |
| Zooming speed        | 4.0s          |
| Lens correction      | 100%          |
| Low pass filter*     | On — 50.00 Hz |
| IMU orientation      | XYZ           |
| Integration method   | None          |
| Códec de exportación | H.265/HEVC    |
| Tamaño de salida     | 4096 × 2304   |
| Bitrate              | 95 Mbps       |
| GPU encoding         | On            |
*A veces utilizo el low pass filter para eliminar ruidos eléctricos o mecánicos que el gyro de la cámara captura en ciertos niveles de throttle.

*Todos los demás settings quedan por defecto.*

## Color en DaVinci Resolve

Uso D-Cinelike en cámara y DaVinci Resolve para la corrección de color. Es el área donde más sigo aprendiendo y donde menos tengo para compartir todavía. Lo documentaré por separado cuando tenga un flujo de trabajo replicable.

## Resultados

Aquí un clip de la costa peruana con estos settings aplicados (Filtros ND 16, 1/60 shutter speed, Gyroflow al 5%, corrección de color en DaVinci):

![Resultado](images/output.gif)

{{< youtube MYRd_c3luvw >}}

---

*Estos settings los desarrollé volando en la costa del Pacífico peruano: sol intenso, terreno de alto contraste, altitud al nivel del mar. En otras condiciones los filtros ND van a variar, pero la lógica es la misma.*