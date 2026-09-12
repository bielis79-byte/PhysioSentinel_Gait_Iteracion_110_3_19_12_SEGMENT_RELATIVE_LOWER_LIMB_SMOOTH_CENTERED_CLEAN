# PhysioSentinel Gait · V110.3.19.6

## Lower-Limb q(t) Propagation Fix

- Mantiene íntegro el pipeline automático validado en V110.3.19.5: 75F → `skin_verts(t)` → malla SKEL → reproductor → NPZ/vídeo.
- Corrige únicamente la propagación temporal de miembros inferiores antes de `skin_verts(t)`.
- Sustituye el rescate inferior basado en posiciones absolutas por un solver DLS basado en vectores relativos de segmento:
  - cadera→rodilla,
  - rodilla→tobillo,
  - cadera→tobillo.
- La traslación corporal común deja de penalizar la articulación de la pierna cuando pelvis/transformación global están congeladas.
- Optimiza q3..q6 para la pierna derecha y q10..q13 para la izquierda; q7/q14 se mantienen si no existe un landmark distal observable con sensibilidad real.
- Usa ponderación XYZ según modalidad (monocular/biplanar estimada/3D calibrada) y continuidad temporal respecto al frame previo.
- El commit se decide por mejora de geometría relativa de la propia pierna, no por el RMSE absoluto global.
- La auditoría existente de `q(t)` y movimiento de RKnee/RAnkle/LKnee/LAnkle se conserva para detectar cualquier congelamiento residual.
- No modifica SKEL24, sexo, B2/manual fallback, gate por modalidad, generación de malla ni exportaciones.
