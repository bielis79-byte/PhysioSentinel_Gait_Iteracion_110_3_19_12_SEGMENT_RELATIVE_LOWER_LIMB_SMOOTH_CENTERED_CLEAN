# V110.3.19.11 · SKEL Lower Limb Motor Isolation

Esta iteración separa dos problemas que hasta ahora estaban mezclados:

1. **Motor SKEL**: q(t) -> `SKEL.forward()` -> `skin_verts(t)` -> reproductor.
2. **Retargeting**: V104/V107 -> q(t).

La nueva prueba `SKEL Lower Limb Motor Test` modifica directamente las articulaciones inferiores en una secuencia sintética alternante. Si la malla mueve ambas piernas, el motor SKEL queda validado y cualquier congelación de la marcha real debe buscarse en la conversión de landmarks a q(t).

Además se recupera de V110.2.4 la semilla geométrica de flexión de rodilla (`pi - ángulo cadera-rodilla-tobillo`) como fallback cuando el solver inferior no modifica sus q.
