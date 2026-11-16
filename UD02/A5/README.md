# A5. Comentarios y anidación

## Errores
1. El comentario está mal escrito: `<!- ... -\>`. Debe abrirse con `<!--` y cerrarse con `-->`.
2. Las etiquetas anidadas se cierran en el orden equivocado: `<strong><em>...</strong></em>`. Se cierra primero la última que se abrió: `</em></strong>`.

## Código corregido
```html
<!-- Revisar el texto antes de publicar -->
<p>Tu contraseña debe tener <strong><em>al menos 12 caracteres</em></strong>.</p>
```