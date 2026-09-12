# V110.3.19.4 · Atomic 75F Persistence + Auto-Recovery + NPZ/Video Downloads

- Restaura el flujo automático validado: Frame 1 PASS → 75F → skin_verts → malla → reproductor → descargas.
- Persistencia atómica en `/tmp`: `.part` + `fsync` + `os.replace`; no depende sólo de `session_state`.
- Caché aislada por fingerprint del registro V104/V107 + sexo SKEL para evitar mezclar pacientes.
- Si un rerun/reconexión ocurre tras 75F, recupera `q(t)` y genera automáticamente la malla sin repetir el fitting temporal.
- Si la malla ya existe, la abre directamente y oculta la necesidad de recalcular 75F.
- Genera y persiste el NPZ inmediatamente al completar la malla.
- Botón destacado `DESCARGAR MARCHA SKEL 75F (.NPZ)`.
- Conserva reproductor y descarga de vídeo SKEL de V110.3.19.1.
- No modifica SKEL24, Unified Coordinate Frame, retargeting, gate ni solver biomecánico.
