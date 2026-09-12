# V110.3.19.9 · Frozen V110.3.19.7 Mesh Flow + Fast Lower-Limb q(t)

Objetivo doble:
1. recuperar de forma estricta el flujo de V110.3.19.7 que sí generaba la malla tras 75/75;
2. corregir la causa demostrada por NPZ de las piernas congeladas: q3-q14 sin variación temporal.

La regla de esta versión es quirúrgica: el control de flujo 75F -> skin_verts -> malla -> reproductor -> NPZ procede de V110.3.19.7. El único cambio funcional relevante está dentro del cálculo de q(t) inferior.

El solver V110.3.19.9 usa cambios de vectores segmentarios entre frames consecutivos para evitar que el sesgo morfológico absoluto V104/V107 vs SKEL favorezca q constante. Se limita a dos pasos DLS por lado para no consumir el presupuesto de ejecución antes de que empiece `skin_verts(t)`.

La malla debe generarse incluso si la auditoría de piernas indica REVISAR; esa auditoría no es una puerta de bloqueo.
