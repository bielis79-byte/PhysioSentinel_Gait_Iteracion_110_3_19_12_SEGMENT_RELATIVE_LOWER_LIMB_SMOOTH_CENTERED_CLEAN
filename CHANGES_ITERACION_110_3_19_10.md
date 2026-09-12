# PhysioSentinel Gait · V110.3.19.10

## SKEL Minimal Direct Pipeline

Objetivo: maximizar la probabilidad de completar la marcha anatómica eliminando del camino SKEL toda persistencia/recuperación de secuencia o malla y toda migración/importación de NPZ.

Cambios:
- Base funcional de flujo: V110.3.19.7.
- Solver de miembros inferiores: V110.3.19.9 (frame-delta DLS rápido).
- Eliminadas funciones `_v193_*` / `_v194_*` de persistencia de secuencia, malla, auditoría y NPZ.
- Eliminado cargador/migrador de NPZ existente.
- Eliminada recuperación automática desde disco/cache de resultados 75F o malla.
- No se escribe manifiesto de estado de marcha.
- `st.session_state` es el único estado temporal durante la sesión activa.
- Flujo crítico directo: Frame 1 PASS → `_fit_skel_sequence()` → q(t) → `_build_skel_skin_sequence()` → `skin_verts(t)` → malla → reproductor.
- La auditoría de miembros inferiores continúa siendo diagnóstica y no bloquea la malla.
- El NPZ final se construye únicamente en memoria para el botón de descarga; no se guarda ni se reutiliza automáticamente.
- Se mantiene únicamente la caché del bundle/modelo SKEL/B2, que pertenece a la carga del modelo y no a la secuencia cinemática.
