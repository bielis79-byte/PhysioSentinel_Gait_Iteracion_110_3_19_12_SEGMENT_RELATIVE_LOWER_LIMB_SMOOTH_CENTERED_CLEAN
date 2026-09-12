# PhysioSentinel Gait V110.3.19.12

## SKEL Segment-Relative Lower-Limb Retargeting

- Base: V110.3.19.11 / pipeline directo sin persistencia ni migración NPZ.
- Cadera: q3-q5 y q10-q12 se obtienen por cambio de orientación Hip→Knee respecto al frame semilla.
- La sensibilidad de cada q se calibra una sola vez contra el `forward()` real de SKEL y se usa durante los 75 frames.
- Rodilla: q6/q13 conserva el cálculo geométrico `pi - angle(Hip,Knee,Ankle)` validado en V110.3.19.11.
- No se acumulan deltas frame-a-frame: cada pose inferior se ancla al frame inicial para evitar deriva.
- Suavizado temporal de q3-q6/q10-q13 con filtro FIR simétrico de dos pasadas y mezcla conservadora con la señal original.
- Tras el suavizado se recalculan los joints SKEL antes de generar `skin_verts`.
- Visor: centra en pelvis y aplica una base anatómica visual fija (X mediolateral, Y progresión, Z vertical) derivada del primer frame.
- La transformación visual no modifica las coordenadas científicas almacenadas en el NPZ.
- Se mantiene el handoff directo 75/75 → `skin_verts` → malla; auditorías no bloqueantes.
