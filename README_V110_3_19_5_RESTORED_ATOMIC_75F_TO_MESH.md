# V110.3.19.5 · Restored V110.3.13 Atomic 75F→Mesh Pipeline

Esta versión toma como referencia directa la orquestación de V110.3.13, donde la propagación temporal y la generación de la malla ocurrían en una única ejecución del botón principal.

## Regla de ejecución

1. Validar Frame 1.
2. Calcular la secuencia temporal de poses SKEL hasta 75 frames.
3. Guardar inmediatamente la secuencia en `session_state` y persistencia atómica `/tmp`.
4. Si existe al menos un 90 % de poses válidas, llamar inmediatamente a `_build_skel_skin_sequence(...)` sin `st.rerun()` intermedio.
5. Guardar malla, auditoría y NPZ.
6. Mostrar reproductor y descargas en la misma ejecución.

La auditoría de movimiento de miembros inferiores se conserva, pero ya no puede bloquear por sí sola la construcción de la malla. Si detecta una anomalía se muestra como advertencia para inspección visual y auditoría posterior.

No se modifican los parámetros biomecánicos ni el ajuste del Frame 1 respecto a V110.3.19.4.
