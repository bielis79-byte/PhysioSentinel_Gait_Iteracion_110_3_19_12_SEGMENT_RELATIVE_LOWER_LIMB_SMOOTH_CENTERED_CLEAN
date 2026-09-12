# PhysioSentinel Gait · V110.3.19.11

## SKEL Lower Limb Motor Isolation + V110.2.4 hinge fallback

- Base: V110.3.19.10 Minimal Direct SKEL, sin persistencia/migración NPZ en el camino crítico.
- Añade una prueba motora aislada de SKEL que anima directamente q3/q6/q7 y q10/q13/q14, ejecuta el `forward()` oficial y genera `skin_verts`.
- El test permite decidir si SKEL + skinning + reproductor pueden mover físicamente las piernas sin depender de V104/V107.
- Recupera el principio de V110.2.4 para las bisagras de rodilla: `knee_angle = pi - angle(Hip,Knee,Ankle)`.
- Ese seed se usa como fallback si el solver inferior produce un delta de q prácticamente nulo.
- Registra `q_before_lower`, `q_after_lower` y el detalle del fallback por frame.
- No añade persistencia, reruns ni carga de NPZ entre 75F y `skin_verts`.
