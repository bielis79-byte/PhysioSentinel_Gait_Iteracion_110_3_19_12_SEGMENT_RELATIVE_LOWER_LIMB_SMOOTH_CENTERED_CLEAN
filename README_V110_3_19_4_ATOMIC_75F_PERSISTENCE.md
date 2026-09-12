# V110.3.19.4

Objetivo: impedir que una secuencia ya calculada 75/75 se pierda al finalizar el rerun de Streamlit.

Flujo esperado:

`Frame 1 PASS → Procesar 75F (una vez) → persistencia atómica de poses → generar skin_verts → persistencia malla/NPZ → abrir reproductor → descargar NPZ/vídeo`.

En reruns posteriores de la misma instancia, el resultado se recupera automáticamente por fingerprint del registro y sexo. Si sólo existe la secuencia 75F, la malla se reconstruye desde las poses persistidas sin repetir el retargeting temporal.

La persistencia `/tmp` dura mientras viva la instancia Streamlit. El NPZ descargado es el mecanismo portable entre despliegues/instancias.
