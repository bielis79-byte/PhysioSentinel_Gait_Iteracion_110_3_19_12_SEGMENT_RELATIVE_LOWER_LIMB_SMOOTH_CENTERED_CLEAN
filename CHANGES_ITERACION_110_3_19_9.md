# PhysioSentinel Gait · V110.3.19.9

## V110.3.19.7 funcional + solver inferior quirúrgico

- Base reconstruida directamente desde V110.3.19.7, la última versión confirmada por el usuario que completaba 75F -> `skin_verts(t)` -> malla SKEL.
- El flujo de Streamlit posterior al retargeting se conserva sin cambios de control respecto a V110.3.19.7; sólo se actualizan etiquetas/versionado.
- Se sustituye únicamente el rescate temporal de miembros inferiores dentro de `_fit_skel_sequence()`.
- Nuevo solver `_lower_limb_delta_tracking_199_fast(...)`:
  - parte siempre de q(t-1) para q3-q7 y q10-q14;
  - usa el delta frame-a-frame de Hip->Knee y Knee->Ankle;
  - resuelve q3-q6 y q10-q13;
  - máximo 2 pasos DLS por lado para reducir de forma importante el coste temporal de V110.3.19.8;
  - commit directo sobre la misma `pose` que se guarda en la secuencia y alimenta `skin_verts(t)`;
  - cualquier excepción del solver es diagnóstica/no bloqueante y nunca impide llegar a la malla.
- q7/q14 permanecen heredados del frame previo salvo refinamiento compatible; el landmark de tobillo `talus` no observa de forma directa el DOF distal de tobillo.
- La auditoría de miembros inferiores continúa siendo informativa y NO bloquea la generación de malla.
- No se añade persistencia, rerun, manifiesto ni auditoría bloqueante entre 75/75 y `_build_skel_skin_sequence()`.
