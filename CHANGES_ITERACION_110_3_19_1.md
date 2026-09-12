# V110.3.19.1 · Immediate Sex Binding + Video Downloads

- Corrige la sincronización Sexo general → SKEL eliminando `patient_sex_live_widget`.
- El selector Sexo queda fuera del `st.form` y actualiza inmediatamente `st.session_state['patient_sex']`.
- SKEL lee exclusivamente `patient_sex`: Mujer → `female` → `skel_female.pkl`; Hombre → `male` → `skel_male.pkl`.
- No existe selector independiente de sexo dentro del flujo SKEL.
- Añade botón `⬇ Vídeo SKEL` en el reproductor anatómico 3D. La grabación se realiza en el navegador sobre el canvas WebGL y descarga MP4 cuando el navegador lo soporta o WEBM como fallback.
- Añade bloque `Todos los vídeos disponibles` en Exportar/Descargar con descargas individuales y ZIP de vídeos generados/cargados en sesión.
- No modifica SKEL24, Unified Coordinate Frame, retargeting, solver temporal ni generación de `skin_verts`.
