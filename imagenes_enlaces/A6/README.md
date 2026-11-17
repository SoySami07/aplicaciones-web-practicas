# Nivel 2 · A6. Rutas que no funcionan

Desde `index.html`:

| Código | ¿Funciona? | Corrección |
|---|---|---|
| `<img src="logo.png" alt="Logo">` | No: `logo.png` está dentro de `imagenes/`. | `<img src="imagenes/logo.png" alt="Logo">` |
| `<img src="imagenes/equipo.jpg" alt="Equipo">` | Sí | — |
| `<a href="Contacto.html">Contacto</a>` | No (en servidores que distinguen mayúsculas): el archivo es `contacto.html`. | `<a href="contacto.html">Contacto</a>` |
| `<a href="apuntes.pdf">Apuntes</a>` | Sí | — |
| `<a href="imagenes/apuntes.pdf">Apuntes</a>` | No: `apuntes.pdf` está en la carpeta principal. | `<a href="apuntes.pdf">Apuntes</a>` |
| `<img src="imagenes/equipo.png" alt="Equipo">` | No: la imagen es `.jpg`, no `.png`. | `<img src="imagenes/equipo.jpg" alt="Equipo">` |