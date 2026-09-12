# PhysioSentinel Gait · V110.3.19.7

## Strict V110.3.13 75F→Mesh Flow

- Restaura de forma estricta la propiedad esencial del flujo V110.3.13: `_fit_skel_sequence()` → `session_state` → `_build_skel_skin_sequence()` sin persistencia, manifiestos ni `st.rerun()` entre ambas fases.
- La persistencia atómica, el manifiesto y el NPZ se ejecutan únicamente después de que la malla ya exista en memoria.
- Un fallo de persistencia secundaria ya no puede borrar ni la secuencia 75F ni la malla generada.
- Las auditorías posteriores a 75/75 pasan a ser no bloqueantes: cualquier excepción se registra, pero la secuencia se conserva para el handoff a `skin_verts(t)`.
- Si `skin_verts(t)` falla, la secuencia q(t) se conserva para regenerar la malla sin repetir el fitting 1→75.
- Mantiene íntegra la corrección V110.3.19.6 de propagación q(t) de miembros inferiores.
