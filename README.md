# Entrega Sesión 7 — Mis Canales Alternativos

Presentación ejecutiva interactiva del programa **Reactiva Emprendedores Univalle**
(Universidad del Valle · Vicerrectoría de Extensión y Proyección Social),
Sesión 7: Ventas y Canales.

Todo el contenido vive en un único archivo HTML autocontenido:

```
presentaci_n_ejecutiva_mis_canales_alternativos.html
```

## ⚠️ Dónde poner el logo

El HTML **no** incluye un logo dibujado: apunta a un archivo de imagen que debes subir tú.

| Qué | Dónde |
| --- | --- |
| Carpeta | `assets/` (en la raíz del repositorio, junto al HTML) |
| Nombre esperado | `assets/logo.png` |
| Etiqueta que lo usa | `<img src="assets/logo.png" ...>` dentro del `<header>` |

Pasos:

1. Crea la carpeta `assets/` si no existe.
2. Copia tu logo ahí y llámalo exactamente `logo.png`
   (si usas otro nombre o formato, por ejemplo `logo.svg`, cambia el `src`).
3. Abre el HTML. El logo aparece en un círculo arriba a la izquierda.
4. El mismo archivo se usa como favicon de la pestaña del navegador.

Mientras el archivo no exista, el HTML muestra un recuadro de respaldo con el texto
`LOGO / assets/logo.png` en lugar de romperse. Ese respaldo desaparece solo al
detectar la imagen.

Para cambiar la ruta hay **dos** referencias que deben coincidir:

```
línea   9   <link rel="icon" type="image/png" href="assets/logo.png">
línea 203   <img src="assets/logo.png" ...>
```

Búscalas con:

```bash
grep -n "assets/logo.png" presentaci_n_ejecutiva_mis_canales_alternativos.html
```

Recomendaciones para la imagen: PNG con fondo transparente, recorte cuadrado,
mínimo 256×256 px. Se muestra con `object-contain` dentro de un círculo de
96–112 px, así que un logo muy apaisado se verá pequeño.

## Cómo verla

Solo abre el archivo en el navegador. También puedes servirlo:

```bash
python3 -m http.server 8000
# http://localhost:8000/presentaci_n_ejecutiva_mis_canales_alternativos.html
```

Se necesita conexión a internet la primera vez porque Tailwind CSS y las fuentes
de Google se cargan por CDN.

## Funcionalidad

- **Tres pestañas**: Diagnóstico Inicial, Selección de Canal y Decisión Estratégica,
  más una vista completa con todo el contenido.
- **Matriz de criterios interactiva**: al hacer clic (o pulsar Enter/Espacio) en un
  criterio se muestra su análisis comparativo. Instagram 21/25 vs. Ferias 13/25.
- **Gráfico de radar** en `<canvas>` que compara ambos canales en cinco criterios.
- **Modo Presentación**: muestra una sección a pantalla completa con controles y
  navegación por teclado (flechas, Espacio, RePág/AvPág, Inicio/Fin, Esc para salir).
- **Imprimir / Guardar PDF**: la hoja de estilos de impresión muestra las tres
  secciones, sin controles ni sombras.

## Accesibilidad

- Pestañas con `role="tab"` / `role="tabpanel"` y `aria-selected`.
- Criterios navegables con teclado (`role="button"`, `tabindex="0"`).
- Panel de detalle con `aria-live="polite"`.
- El canvas del radar tiene `role="img"`, `aria-label` y una descripción textual.
- Foco visible y respeto a `prefers-reduced-motion`.
