# V110.3.19.10 · Minimal Direct SKEL

Versión diagnóstica orientada a un único objetivo: convertir los 75 frames V104/V107 en una secuencia q(t) y, en la misma sesión, construir `skin_verts(t)` y mostrar la malla anatómica SKEL.

No existe en esta versión ruta de importación/migración de NPZ ni recuperación de secuencia/malla desde disco. Una desconexión o reboot obliga a recalcular los 75 frames, deliberadamente, para evitar que un estado antiguo sustituya la secuencia recién calculada.

El NPZ de salida sigue disponible como descarga científica final, pero se genera al vuelo y no se persiste dentro de la app.
