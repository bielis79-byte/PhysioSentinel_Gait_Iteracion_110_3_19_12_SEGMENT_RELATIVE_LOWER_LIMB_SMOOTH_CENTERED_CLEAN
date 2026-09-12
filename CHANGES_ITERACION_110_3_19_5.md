# PhysioSentinel Gait · V110.3.19.5

## Restored V110.3.13 Atomic 75F→Mesh Pipeline

- Restaura la transición automática que funcionaba en V110.3.13: un único clic ejecuta `q(t) 1→75` y, en la misma ejecución, `skin_verts(t)` y la malla anatómica SKEL.
- Elimina la regresión de V110.3.19.3/.4 en la que el proceso podía alcanzar 75/75 y volver a mostrar el botón rojo sin exponer la malla.
- La auditoría temporal de miembros inferiores deja de bloquear la construcción de `skin_verts(t)`: se conserva como advertencia clínica/técnica para inspección, pero no impide visualizar la malla.
- La malla sólo se omite si no se alcanza el mínimo de poses válidas (90 % de la secuencia esperada).
- Mantiene intactos el retargeting SKEL24 actual, la puerta por modalidad, sexo unificado, correcciones temporales de piernas, B2/manual fallback y NumPy 2.x.
- Mantiene persistencia atómica de secuencia/malla/NPZ y auto-recovery; la persistencia ya no sustituye ni interrumpe el flujo principal.
- Flujo esperado: `Frame 1 PASS → 75F → skin_verts(t) → malla → reproductor → NPZ/vídeo`.
