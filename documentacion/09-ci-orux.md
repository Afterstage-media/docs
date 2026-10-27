# 09 · CI/CD y producción de Afterstage

Este documento reemplaza referencias históricas a Orux o Aurea. Afterstage tiene su propio repositorio de CI/CD y su propia producción.

## Repositorios

- `frontend`: React/Vite y superficie pública.
- `backend`: API, persistencia, integraciones, correo y dominio editorial.
- `afterstage-storage-gateway`: reservas y subidas a R2.
- `ci-cd`: imágenes, manifiestos, Flux y contratos de producción.
- Este repositorio: documentación de producto, UX, seguridad y operación.

## Flujo obligatorio

1. Trabajar en una rama que no sea `main`.
2. Ejecutar formato, build, tests y auditoría de dependencias.
3. Abrir PR y esperar CI verde.
4. Mergear a `main`; nunca publicar directamente en `main`.
5. Construir y escanear las imágenes desde `ci-cd`.
6. Promover tags inmutables en `deploy/afterstage/kustomization.yaml` mediante PR.
7. Esperar el reconcile/rollout de Flux en `underkode`.
8. Verificar `https://afterstage.ar/health`, `/ready`, rutas públicas, logs y consola.

El cluster local debe permanecer apagado. `underkode` es la única producción válida.

## Contratos de publicación

- No promover imágenes sin scan de vulnerabilidades exitoso.
- No llamar “operativa” a una integración que solo tiene código: debe tener credenciales, proveedor, datos y prueba end-to-end.
- No guardar secretos en Git, imágenes, frontend, capturas o logs.
- No desplegar fixtures, datos demo ni contenido editorial inventado.
- Si falta una credencial o decisión externa, registrar el bloqueo y detener esa parte del rollout.

## Verificación productiva mínima

```bash
curl --fail --silent --show-error https://afterstage.ar/health
curl --fail --silent --show-error https://afterstage.ar/ready
curl --fail --silent --show-error https://afterstage.ar/sitemap.xml
```

En `underkode`, usar exclusivamente `KUBECONFIG="$HOME/.kube/afterstage.yaml"` y verificar que los deployments `backend` y `website` estén disponibles con el tag promovido. Consultar [`10 · Estado actual y brechas`](./10-estado-actual-y-brechas.md) para las capacidades que todavía dependen de configuración o contenido real.
