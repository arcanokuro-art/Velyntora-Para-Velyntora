# animation_project_setup

## Estado
Especificación de referencia para la pantalla **Crear animación** de Velyntora.

Esta carpeta NO contiene la implementación final. La implementación real se hará posteriormente en `arcanokuro-art/Velyntora`.

## Exclusivo de
**ANIMACIÓN**

No mezclar esta configuración con `drawing_project_setup`.

## Canvas Size / Tamaño del lienzo

- Ancho en píxeles (px)
- Alto en píxeles (px)
- Relación vinculada para mantener la proporción al modificar ancho o alto

## Presets de Animación

| Preset | Width | Height |
|---|---:|---:|
| YouTube | 1920 px | 1080 px |
| YouTube | 1280 px | 720 px |
| Instagram | 1280 px | 720 px |
| Instagram | 720 px | 720 px |
| TikTok | 1080 px | 1920 px |
| TikTok | 720 px | 1280 px |
| Vimeo | 1920 px | 1080 px |
| Facebook | 1280 px | 720 px |
| Tumblr | 540 px | 304 px |
| Tumblr | 540 px | 404 px |

## Frames per second

La pantalla **Crear animación** tendrá un desplegable para seleccionar la velocidad del proyecto.

Valores disponibles:

`1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30 FPS`

El comportamiento visual de selección se inspira en la configuración de creación de proyectos estudiada en FlipaClip, pero la implementación de Velyntora será propia.

## Flujo

```text
Inicio de Velyntora
    ↓
ANIMACIÓN
    ↓
Crear animación
    ↓
Configurar ancho y alto
    ↓
Opcional: mantener relación vinculada
    ↓
Elegir preset o dimensiones manuales
    ↓
Elegir FPS (1–30)
    ↓
Crear proyecto de animación
```

## Separación obligatoria

`animation_project_setup` pertenece únicamente al flujo **Crear animación**.

No debe reutilizar la lista de presets de Dibujo como si ambas pantallas fueran una sola configuración. Los FPS existen aquí y NO en Crear ilustración.

## Destino

Implementación futura: `arcanokuro-art/Velyntora`.

`Velyntora-Z` queda fuera de este proceso y no debe modificarse.
