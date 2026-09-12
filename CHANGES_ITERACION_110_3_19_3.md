# V110.3.19.3 · Persistent 75F Result + Auto-Open SKEL Mesh + NPZ/Video Download Fix

- Conserva el resultado temporal de 75 frames en `session_state` y en caché `/tmp` durante la vida de la instancia Streamlit.
- Si el resultado 75F ya existe, oculta el recálculo y abre directamente la marcha/malla SKEL.
- Conserva también la malla 6890 vértices/frame y su auditoría en caché runtime.
- Mantiene descarga científica NPZ de la malla (`vertices`, `faces`, `joints`, `frame_ids`, escala y betas).
- Mantiene los controles de descarga de vídeo incorporados en V110.3.19.x.
- No modifica el retargeting, el mapa SKEL24 ni la puerta anatómica validada de V110.3.19.2.
