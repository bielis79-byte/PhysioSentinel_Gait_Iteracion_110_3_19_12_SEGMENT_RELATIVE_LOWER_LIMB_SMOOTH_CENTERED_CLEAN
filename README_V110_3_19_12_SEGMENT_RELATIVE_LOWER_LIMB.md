# V110.3.19.12 · Segment-Relative Lower Limb

Objetivo: convertir el movimiento de V104/V107 en movimiento coordinado de cadera y rodilla SKEL sin depender de coincidencia cartesiana absoluta ni acumular errores entre frames.

Cadena de cálculo:

`Hip→Knee(t) vs Hip→Knee(frame inicial)` → sensibilidad real SKEL q cadera → q3-q5 / q10-q12

`Hip-Knee-Ankle(t)` → flexión geométrica de rodilla → q6 / q13

`q inferiores crudos` → suavizado temporal → `SKEL.forward()` → `skin_verts(t)` → malla

El tobillo q7/q14 no se fuerza en esta iteración porque el landmark R/LAnkle se corresponde con el talus y no aporta una observación distal suficiente para estimar de forma robusta el DOF del tobillo. Se prioriza una cadena cadera-rodilla coherente antes de añadir pie/retropié.

El visor aplica únicamente una transformación de presentación centrada en pelvis y orientada en ejes anatómicos. El NPZ conserva las coordenadas originales.
