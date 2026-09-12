# PhysioSentinel Gait V110.3.19.1

Parche correctivo sobre V110.3.19.

## Sexo unificado inmediato
El campo `Sexo` de la ficha general es la única fuente de verdad y se aplica en el mismo rerun a SKEL. No depende de pulsar `Guardar datos`.

- Mujer → female → skel_female.pkl
- Hombre → male → skel_male.pkl

## Descargas de vídeo
El panel Exportar/Descargar muestra todos los MP4 disponibles en la sesión y permite descargar un ZIP con ellos. El reproductor SKEL incorpora `⬇ Vídeo SKEL`, que graba la animación 3D WebGL completa directamente en el navegador.

La captura de la malla puede salir como MP4 o WEBM según la compatibilidad MediaRecorder del navegador.
