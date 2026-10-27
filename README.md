# Afterstage — documentación de producto

Repositorio de documentación del ecosistema Afterstage.

Incluye la visión del producto, arquitectura, sistema visual, UX, seguridad,
operación y decisiones técnicas. El código ejecutable vive en repositorios
separados:

- [frontend](https://github.com/medio-under/frontend)
- [backend](https://github.com/medio-under/backend)
- [ci-cd](https://github.com/medio-under/ci-cd)

## Documentos

- `01-vision.md`: propósito, audiencia y propuesta de valor.
- `02-arquitectura.md`: recorridos y arquitectura general.
- `03-sistema-visual.md`: identidad visual y componentes.
- `04-mvp.md`: alcance y evolución del MVP.
- `05-social-manager.md`: arquitectura del backend editorial.
- `06-publicacion-local-cloudflare.md`: ejecución local y túneles.
- `07-seguridad.md`: controles y riesgos residuales.
- `08-agenda-eventos.md`: agenda y fuentes externas.
- `09-ci-orux.md`: integración y automatización CI/CD.
- `10-estado-actual-y-brechas.md`: contraste entre la expectativa de producto, la implementación y la operación real.

## Fuente de verdad y límites

Afterstage combina medio editorial, red profesional y agenda/infraestructura de
eventos. `frontend/` es la superficie pública, `backend/` contiene la API y
`ci-cd/` gobierna el despliegue GitOps en el cluster `afterstage` de
`underkode`. Este repositorio no debe desplegarse como una segunda aplicación
ni usarse para afirmar que una capacidad está operativa.

Cada revisión debe distinguir:

- **Implementado:** existe código y prueba automatizada.
- **Publicado:** llegó a `main` y al rollout productivo.
- **Operativo:** también tiene datos reales, credenciales, responsables y una prueba end-to-end.
- **Bloqueado:** falta una decisión, proveedor, credencial o dato que no debe inventarse.
