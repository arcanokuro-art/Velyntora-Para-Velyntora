# drawing_project_setup

## Estado
Especificación de referencia para la pantalla **Crear ilustración** de Velyntora.

Esta carpeta NO contiene la implementación final. La implementación real se hará posteriormente en `arcanokuro-art/Velyntora`.

## Exclusivo de
**DIBUJO**

No mezclar esta configuración con `animation_project_setup`.

## Canvas Size / Tamaño del lienzo

- Ancho en píxeles (px)
- Alto en píxeles (px)
- Relación vinculada para mantener la proporción al modificar ancho o alto

## Presets de Dibujo

| Preset | Width | Height |
|---|---:|---:|
| YouTube | 1920 px | 1080 px |
| YouTube | 1280 px | 720 px |
| TikTok | 1080 px | 1920 px |
| TikTok | 720 px | 1280 px |
| Pixiv | 1700 px | 2400 px |
| Dojinshi | 4299 px | 6071 px |
| Manga | 4960 px | 7016 px |

## Frames per second

**No aplica.**

Crear ilustración no tendrá selector de FPS.

## Flujo

```text
Inicio de Velyntora
    ↓
DIBUJO
    ↓
Crear ilustración
    ↓
Configurar ancho y alto
    ↓
Opcional: mantener relación vinculada
    ↓
Elegir preset o dimensiones manuales
    ↓
Crear ilustración
```

## Separación obligatoria

`drawing_project_setup` pertenece únicamente al flujo **Crear ilustración**.

No debe mostrar FPS ni utilizar automáticamente los presets exclusivos de Animación.

## Destino

Implementación futura: `arcanokuro-art/Velyntora`.

`Velyntora-Z` queda fuera de este proceso y no debe modificarse.
