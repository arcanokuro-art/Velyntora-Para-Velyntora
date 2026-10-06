# auto_inbetween_animation

## Estado
Herramienta de referencia/análisis para Velyntora. **Exclusiva del entorno ANIMACIÓN.**

Este directorio no contiene la implementación final de Velyntora. Documenta el comportamiento y la arquitectura necesarios para construir una versión propia posteriormente en `arcanokuro-art/Velyntora`.

## Objetivo
Permitir que el usuario dibuje dos fotogramas extremos y genere automáticamente dibujos intermedios cuando el contenido sea compatible con interpolación.

Ejemplo:

```text
Frame 1      Frames 2-11 vacíos      Frame 12
[Dibujo A]  ---------------------->  [Dibujo B]
                  Auto Inbetween
                         ↓
          genera los estados intermedios
```

## Referencia estudiada: OpenToonz 1.8.0
En el código fuente analizado de OpenToonz se identificó el sistema Inbetween / Auto Inbetween.

Componentes relevantes observados:

- `TInbetween`
- `tinbetween.h`
- `tinbetween.cpp`
- `FilmstripCmd::inbetween(...)`
- `FilmstripCmd::inbetweenWithoutUndo(...)`
- `TVectorImage`
- `TStroke`

La función interpola dibujos vectoriales y sus trazos entre dos extremos.

## Modos de interpolación observados
- Linear
- Ease In
- Ease Out
- Ease In/Out

## Flujo funcional propuesto para Velyntora

```text
fotograma inicial
       +
fotograma final
       ↓
validar compatibilidad
       ↓
seleccionar rango de frames
       ↓
seleccionar tipo de interpolación
       ↓
calcular progreso t para cada frame
       ↓
interpolar trazos/propiedades
       ↓
crear nuevos dibujos intermedios
       ↓
insertarlos en el timeline de Animación
       ↓
permitir Undo/Redo
```

## Propiedades candidatas a interpolación
Según el comportamiento estudiado, una implementación propia puede considerar:

- posición
- escala
- rotación
- geometría del trazo
- puntos de control
- grosor
- correspondencia entre trazos

## Restricción importante
El Auto Inbetween estudiado no debe interpretarse como una IA capaz de inventar cualquier dibujo raster entre dos imágenes arbitrarias.

La referencia de OpenToonz trabaja principalmente con imágenes/trazos vectoriales (`TVectorImage`, `TStroke`). Velyntora deberá validar qué contenidos pueden interpolarse correctamente y comunicarlo claramente al usuario.

## Arquitectura recomendada para la implementación propia

1. **Animation Timeline Integration**
   - seleccionar frame inicial y final
   - detectar frames intermedios
   - insertar resultados

2. **Compatibility Analyzer**
   - validar los dos extremos
   - determinar correspondencias entre trazos

3. **Interpolation Engine**
   - calcular `t` para cada frame
   - Linear / Ease In / Ease Out / Ease In-Out
   - interpolar geometría y propiedades

4. **Generated Frame Writer**
   - crear el contenido de cada frame
   - conservar orden y datos de capa

5. **History Integration**
   - Undo/Redo de toda la generación como una operación coherente

6. **Error/Conflict Handling**
   - evitar sobrescribir frames ocupados sin confirmación
   - manejar dibujos incompatibles
   - cancelar sin dejar estados parciales

## Clasificación dentro de Velyntora

```text
VELYNTORA
├── DIBUJO
│   └── Auto Inbetween: NO
└── ANIMACIÓN
    ├── video_to_frames_animation
    └── auto_inbetween_animation
```

## Destino
Cuando se autorice su implementación, se programará una versión propia adaptada a la arquitectura Android/Java y al timeline de Animación de:

`arcanokuro-art/Velyntora`

## Repositorios
- `Velyntora-Para-Velyntora`: análisis/especificación de la herramienta.
- `Velyntora`: futura implementación real.
- `Velyntora-Z`: fuera de este proceso; no modificar.
