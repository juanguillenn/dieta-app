# Dieta privada

Dashboard móvil publicado con GitHub Pages. El repositorio y la web no contienen
la dieta ni un enlace al Excel. Cada usuario selecciona su propio `.xlsm`, `.xlsx`
o `.xls`; el archivo se procesa localmente en el navegador y la copia de trabajo,
las notas y las preferencias permanecen en el almacenamiento de ese dispositivo.

GitHub Pages solo sirve el código estático. Para actualizar la dieta, pulsa el
botón de importar y vuelve a seleccionar el Excel fuente. El archivo fuente no se
modifica ni se sube desde la aplicación.

En iPhone puede instalarse desde Safari con “Añadir a pantalla de inicio”. En ese
modo usa toda la zona segura. En una pestaña normal, Safari conserva sus propias
barras del navegador, que una web no puede ocultar.

## Pruebas

```sh
npm test
```
