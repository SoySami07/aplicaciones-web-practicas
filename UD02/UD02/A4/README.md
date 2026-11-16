# A4. Estilos rotos

| Línea | Qué falla | Corrección |
|---|---|---|
| 1 | Falta el `;` entre `color:red` y `font-size:40px`, así que el navegador no entiende los dos pares. | `<h1 style="color:red; font-size:40px;">Directo esta noche</h1>` |
| 2 | Se ha escrito `text-align=center` con `=`. En CSS propiedad y valor se separan con `:`. | `<p style="text-align:center;">Estreno de temporada</p>` |
| 3 | La etiqueta final es `<p>` (apertura) en lugar de `</p>` (cierre). | `<p style="background-color:yellow;">Sorteo de una tarjeta gráfica</p>` |