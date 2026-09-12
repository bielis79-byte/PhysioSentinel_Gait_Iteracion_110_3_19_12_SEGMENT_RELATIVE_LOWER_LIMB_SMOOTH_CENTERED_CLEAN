# V110.3.19.6 · Lower-Limb q(t) Propagation Fix

Objetivo: resolver el hallazgo objetivo de V110.3.19.5: el target V104/V107 mostraba movimiento de rodillas/tobillos, mientras q3..q7 y q10..q14 permanecían constantes y los joints inferiores SKEL tenían recorrido 0.

La corrección actúa sólo en `_fit_skel_sequence()`. Después del refinamiento temporal general se ejecuta `_lower_limb_vector_dls_196()`, que ajusta la forma relativa de cada pierna eliminando la traslación común del cuerpo. El solver usa los vectores hip→knee, knee→ankle y hip→ankle y escribe el resultado directamente en la misma `pose` que se persiste y alimenta `SKEL.forward()`/`skin_verts(t)`.

## Validación esperada

1. El flujo V110.3.19.5 debe seguir llegando automáticamente a 75/75 y después a la malla.
2. `pose_sequence_integrity` no debe informar `q pierna derecha constante` ni `q pierna izquierda constante` cuando el target inferior se mueve.
3. RKnee/RAnkle/LKnee/LAnkle deben presentar recorrido temporal SKEL > 0 cuando el target presenta recorrido > 0.
4. La malla debe mostrar flexo-extensión visible de cadera/rodilla durante la marcha.
5. Si la auditoría sigue fallando, conservar el NPZ para medir qué q siguen constantes antes de introducir cualquier otra modificación.
