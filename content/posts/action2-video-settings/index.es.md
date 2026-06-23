---
title: "Mis ajustes de video en la DJI Action 2 para vuelos FPV de proximidad"
date: 2026-06-22
draft: false
tags: ["camara", "action2", "ajustes", "motion blur", "fpv"]
summary: "Sin perfil logarítmico ni 10 bits, pero con los ajustes correctos la DJI Action 2 sigue entregando excelente footage para FPV. Esto es lo que uso y por qué."
---

El objetivo era simple: capturar la velocidad del vuelo y la belleza del paisaje. Motion blur, buena exposición, campo visual amplio. Llegar ahí tomó algunas iteraciones.

Este post documenta los ajustes que uso para lograrlo con la DJI Action 2. Las dos decisiones clave: romper la regla del obturador a 180° y reducir drásticamente la estabilización en cámara.

## Ajustes base

- **Resolución:** 4K 60fps, formato 4:3.
- **FOV:** Wide (no Ultra Wide). Esto preserva los datos del giroscopio para estabilización.
- **Perfil de color:** D-Cinelike.
- **Balance de blancos:** AWB por ahora (sigo experimentando aquí).
- **Estabilización:** Apagar la estabilización en cámara. Todo ocurre en Gyroflow.

![Footage RAW](images/motion-blur.gif)

## El problema de la exposición: cómo lo resolví

La exposición automática es una trampa para vuelo FPV de proximidad. La cámara se mueve constantemente entre cielo brillante y terreno oscuro, y si la dejas decidir, obtienes imágenes quemadas, zonas oscuras, y sin motion blur.

Mi enfoque actual:

- **Velocidad de obturador:** Fija entre 1/60 y 1/80.
- **ISO:** Rango bloqueado entre 100 y 400 (no fijo, no automático completo).
- **Filtros ND:** Indispensables (y elegidos antes de cada vuelo o sesión).

![Action 2 + filtros ND de TBS](images/action2_filter.jpg)

### Cómo elijo el filtro ND

Antes de cada vuelo o sesión hago una prueba corta:

1. Elige un filtro ND y configura la cámara con tus ajustes base.
2. Apunta al cielo y revisa el medidor de exposición.
3. Apunta al suelo o una superficie oscura y revisa de nuevo.
4. Objetivo: medidor de exposición en 0 o muy cerca en ambos extremos.
5. Si sobreexpone al cielo → ND más oscuro.
6. Si subexpone en las sombras → ND más claro.
7. Si ocurren ambos → ajusta ISO o velocidad de obturador primero, luego repite.

Cuando el medidor de exposición está en 0 en ambos extremos, ese es tu ND.

Este ejercicio toma dos minutos y salva el vuelo completo.

## Motion blur: la regla que rompí

La regla estándar para 60fps es obturador a 1/120 (la regla de los 180°). Para la mayoría de grabaciones, es correcta. Para FPV de proximidad, encontré que está equivocada.

A 1/120, el terreno cercano todavía se ve nítido y detallado en vez de fluido. Entre 1/60 y 1/80, obtienes suficiente motion blur para que las pasadas rápidas se vean naturales, manteniendo detalle en tomas más lentas y paisajes.

Esto solo funciona si la selección de ND es correcta. Un obturador más lento con el ND equivocado simplemente quema la imagen. El método de prueba anterior se vuelve crítico aquí.

## Gyroflow: menos es más

Estabilizo en Gyroflow, no en cámara. Pero la decisión clave fue cuánta estabilización aplicar.

Los ajustes por defecto están en 50% de suavidad. Para vuelo FPV de proximidad eso es demasiado: eliminas la sensación de movimiento que hace que el footage valga la pena. Uso entre 5 y 15% según el estilo de vuelo:

- **Suavidad: 5–15%**
  - 5%: corrige el wobble más visible, mantiene la sensación de vuelo.
  - 15%: más suave para pasadas cinematográficas lentas.

![Ajustes de Gyroflow al 5% de suavidad](images/gyroflow.png)

**Mis ajustes actuales:**

| Parámetro | Valor |
|---|---|
| Smoothness | 5.0% |
| Lock horizon | Off |
| Dynamic zooming | On |
| Zoom limit | 115% |
| Zooming speed | 4.0s |
| Lens correction | 100% |
| Low pass filter | On — 50.00 Hz |
| IMU orientation | XYZ |
| Integration method | None |
| Códec de exportación | H.265/HEVC |
| Tamaño de salida | 4096 × 2304 |
| Bitrate | 95 Mbps |
| GPU encoding | On |

*Todo lo demás: por defecto.*

## Corrección de color en DaVinci Resolve

Por ahora no tengo mucho que recomendar aquí. Uso D-Cinelike en cámara y DaVinci Resolve para la corrección de color. Es el área donde más sigo aprendiendo. Lo documentaré por separado cuando tenga algo replicable.

## Resultados

Aquí un clip de la costa peruana con estos ajustes aplicados:

![Resultado](images/output.gif)

{{< youtube MYRd_c3luvw >}}

---

*Estos ajustes fueron desarrollados volando en la costa del Pacífico peruano: sol intenso a mediodía, terreno de alto contraste, altitud al nivel del mar. Otras condiciones requerirán diferentes filtros ND, pero la lógica es la misma.*