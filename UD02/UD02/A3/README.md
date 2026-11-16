# A3. Caza los errores

## Errores encontrados
1. Falta `<!DOCTYPE html>` al principio.
2. Falta el atributo de idioma en `<html>` (`lang="es"`).
3. Falta `<meta charset="utf-8">` en `<head>` (las tildes y la ñ pueden verse mal).
4. `<title>` no está cerrado: falta `</title>`.
5. `<h1>` se cierra con `</h2>`: debe cerrarse con `</h1>`.
6. Mala anidación: `<b>` se abre dentro de `<p>` pero se cierra fuera (`</p></b>`). Hay que cerrar `</b>` antes que `</p>`.
7. Falta `<meta name="author">` (norma general del boletín).

## Código corregido
```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="utf-8">
  <meta name="author" content="Sami ElKhalil Darwish">
  <title>Mi tienda de gadgets</title>
</head>
<body>
  <h1>Ofertas de otoño</h1>
  <p>Auriculares con <b>cancelación de ruido</b></p>
</body>
</html>
```