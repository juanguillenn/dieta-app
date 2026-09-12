# Dieta privada (1.0)

Dieta importa el Excel localmente y no lo sube ni lo modifica. La vista **Compra** agrupa ingredientes y cantidades compatibles, muestra su origen semanal, permite editar la checklist y genera `Producto (cantidad unidad)` para copiar en cualquier dispositivo.

## Envío directo a AnyList

El frontend y el adaptador mínimo se ejecutan en un Cloudflare Worker Free del mismo dominio. Las credenciales sólo existen como secretos del Worker. Como AnyList no ofrece una API pública para este flujo, la integración utiliza el protobuf de la biblioteca comunitaria `anylist`.

1. Crea un namespace KV gratuito para la protección anti-duplicados y configura su identificador como `SEND_STATE` en `wrangler.jsonc`.
2. Crea los secretos `ANYLIST_EMAIL` y `ANYLIST_PASSWORD` con `wrangler secret put`; nunca los guardes en archivos ni en Git.
3. Despliega con `npm run deploy` y comprueba que existe exactamente **Lista de la compra** en AnyList.
4. Crea `DIETA_ACCESS_PASSWORD` y `DIETA_SESSION_SECRET` como secretos. El Worker protege todos los recursos y entrega una cookie de sesión `HttpOnly`, `Secure` y `SameSite=Strict`.
5. Prueba la previsualización antes del primer envío real.

Los artículos ya activos se muestran y se omiten. Los completados se recrean con la cantidad nueva e intentan conservar categoría y tiendas. KV conserva durante 30 días la protección anti-duplicados. **Regenerar compra** inicia conscientemente un envío nuevo.

Si el servidor no está disponible, **Copiar compra** sigue funcionando. Cuando el navegador bloquea el portapapeles aparece un cuadro visible con el texto ya seleccionado.

## Validación

```sh
npm test
npm run check
npx wrangler deploy --dry-run
```
