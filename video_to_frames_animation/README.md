# video_to_frames_animation

## Estado

Herramienta de referencia y análisis para Velyntora.

Este directorio NO contiene una implementación de Velyntora ni código propietario extraído de aplicaciones de terceros. Su objetivo es documentar el comportamiento y los requisitos de la función antes de crear una implementación propia en el repositorio `Velyntora`.

## Objetivo

Importar un archivo de vídeo y transformarlo en una secuencia de fotogramas utilizables en el entorno de Animación de Velyntora.

## Flujo funcional previsto

1. Seleccionar un vídeo.
2. Mostrar una previsualización.
3. Permitir definir el punto inicial y final del fragmento que se desea importar.
4. Leer o seleccionar la tasa de fotogramas (FPS).
5. Calcular previamente la cantidad estimada de fotogramas.
6. Mostrar duración, resolución y cantidad de fotogramas antes de iniciar.
7. Procesar el vídeo sin bloquear la interfaz principal.
8. Extraer/generar los fotogramas.
9. Incorporar los fotogramas resultantes al timeline de Animación de Velyntora.
10. Informar del progreso y permitir manejar cancelación/errores.

## Parámetros principales

- URI/ruta del vídeo.
- Punto de entrada (trim in).
- Punto de salida (trim out).
- FPS de extracción/proyecto.
- Duración.
- Número de fotogramas.
- Límite máximo de fotogramas.
- Anchura y altura del proyecto.
- Progreso de conversión.

## Referencia estudiada

Durante el análisis de paquetes Android de FlipaClip se identificaron nombres y recursos que evidencian una arquitectura de importación de vídeo, entre ellos:

- ImportVideoActivity
- ImportVideoFragment
- ImportVideoWorker
- VideoTrimControlsView
- VideoImportRequest
- PendingVideoImport
- referencias a frameCount, maxFrameCount, FPS, duración y progreso
- componentes multimedia como Media3
- presencia de FFmpeg dentro del stack multimedia

Estos nombres se conservan únicamente como notas de análisis para entender el comportamiento observado. No se incorpora su código ni sus binarios en este directorio.

## Arquitectura recomendada para Velyntora

La implementación propia debería separar:

- UI de selección/previsualización y recorte.
- Modelo de solicitud de importación.
- Motor de decodificación/extracción.
- Trabajo en segundo plano.
- Escritura de los frames en el proyecto/timeline.
- Progreso, cancelación y gestión de errores.

Flujo conceptual:

```text
Video
  |
  v
Seleccion / previsualizacion
  |
  v
Recorte + FPS
  |
  v
Calculo de frames
  |
  v
Worker de conversion
  |
  v
Frames
  |
  v
Timeline de Animacion de Velyntora
```

## Destino posterior

Cuando se decida implementar esta herramienta, se desarrollará una versión propia en:

`arcanokuro-art/Velyntora`

El repositorio `Velyntora-Z`, que contiene la base Krita de referencia, no forma parte de este proceso y no debe modificarse.
