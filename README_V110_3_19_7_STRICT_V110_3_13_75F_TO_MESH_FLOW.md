# V110.3.19.7 · Strict V110.3.13 75F→Mesh Flow

Objetivo: impedir que una operación auxiliar posterior a 75/75 interrumpa la transición a la malla anatómica.

Flujo principal obligatorio:

`Frame 1 PASS → _fit_skel_sequence() → 75/75 → session_state → _build_skel_skin_sequence() → malla visible`

Sólo después de obtener la malla se ejecutan caché, manifiesto, NPZ y demás persistencia. Estas operaciones son best-effort y nunca eliminan el resultado científico ya calculado.

La lógica de retargeting y la propagación q(t) inferior de V110.3.19.6 se mantienen sin cambios.
