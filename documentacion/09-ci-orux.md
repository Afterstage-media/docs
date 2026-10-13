# CI de Orux Solutions

El repositorio actual no apunta a Aurea: ese ecosistema es histórico y no debe
usarse para este medio.

La organización `Orux-Solutions` sólo expone públicamente su repositorio de
perfil `.github` con las credenciales disponibles en este entorno. No hay un
repositorio de CI/release visible para copiar sin inventar una ruta o una
configuración. Cuando se comparta la URL exacta del repo privado de Orux y el
token tenga acceso, se puede comparar y adoptar sus workflows literalmente.

Mientras tanto, el proyecto tiene workflows locales equivalentes y auditables:

- `.github/workflows/release.yml`: versión, tag anotado y GitHub Release.
- `.github/workflows/commit-policy.yml`: validación de Conventional Commits.
- `scripts/calculate-version.sh` y `scripts/validate-commits.sh`: lógica
  reutilizable y testeable sin depender de otra organización.
