# Nivel 2 · A5. Caza los errores de la galería

## Errores encontrados
1. Falta `lang="es"` en la etiqueta `<html>`.
2. Falta `<meta name="author">` en `<head>` (norma del boletín).
3. La primera imagen está mal escrita: `<img>src="playa.jpg" ...</img>`. Los atributos van **dentro** de la etiqueta de apertura y `<img>` no lleva cierre.
4. En el `style` de la segunda imagen se usa `=` en lugar de `:` (`width=300px`). Debe ser `width:300px;`.
5. La segunda imagen no tiene atributo `alt`.
6. El valor de `href` no lleva comillas: `href=https://www.wikipedia.org`.
7. El enlace no se cierra: falta `</a>`.

## Código corregido
```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="author" content="Sami ElKhalil Darwish">
<title>Mi galería</title>
</head>
<body>
<h1>Mi viaje de fin de curso</h1>
<img src="playa.jpg" alt="Playa al atardecer">
<img src="monte.jpg" alt="Monte" style="width:300px; height:200px;">
<a href="https://www.wikipedia.org" target="_blank">Más información sobre el destino</a>
</body>
</html>
```