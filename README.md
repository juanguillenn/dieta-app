# Dieta privada

Dashboard móvil publicado con GitHub Pages. El repositorio y la web no contienen
la dieta ni un enlace al Excel. Cada usuario selecciona su propio `.xlsm`, `.xlsx`
o `.xls`; el archivo se procesa localmente en el navegador y la copia de trabajo,
las notas y las preferencias permanecen en el almacenamiento de ese dispositivo.

GitHub Pages solo sirve el código estático. Para actualizar la dieta, pulsa el
botón de importar y vuelve a seleccionar el Excel fuente. El archivo fuente no se
modifica ni se sube desde la aplicación.

La vista **Compra** consolida los ingredientes de la semana, suma cantidades
compatibles, los agrupa por categorías y guarda localmente la checklist. El botón
**Copiar compra** genera una línea por producto en el formato
`Producto (cantidad unidad)`, listo para pegar en AnyList.

En dispositivos Apple, **Enviar a AnyList** abre el atajo personal
`Enviar a AnyList` y le entrega ese mismo texto. Para configurarlo en iPhone:

1. Instala AnyList e inicia sesión; abre **Atajos** y crea un atajo llamado
   exactamente `Enviar a AnyList`.
2. Añade **Dividir texto**, usa `Entrada del atajo` como texto y selecciona
   **Líneas nuevas** como separador.
3. Añade **Repetir con cada ítem** sobre el resultado de `Dividir texto`.
4. Dentro de la repetición, añade la acción oficial de AnyList para añadir un
   artículo. Usa `Ítem repetido` como nombre y elige la lista de compra destino.
5. Guarda el atajo y ejecútalo una vez desde Atajos para conceder los permisos
   que soliciten iOS o AnyList.

La web entrega cada línea completa (`Producto (cantidad unidad)`) como nombre;
no presupone que AnyList vaya a separar la cantidad. AnyList no ofrece una API
pública para que esta PWA confirme la inserción. Por eso Dieta marca el envío al
lanzar el atajo y bloquea un segundo intento hasta regenerar; si el atajo falla,
regenera antes de reintentarlo. En Android se utiliza la copia al portapapeles.

En iPhone puede instalarse desde Safari con “Añadir a pantalla de inicio”. En ese
modo usa toda la zona segura. En una pestaña normal, Safari conserva sus propias
barras del navegador, que una web no puede ocultar.

## Pruebas

```sh
npm test
```
