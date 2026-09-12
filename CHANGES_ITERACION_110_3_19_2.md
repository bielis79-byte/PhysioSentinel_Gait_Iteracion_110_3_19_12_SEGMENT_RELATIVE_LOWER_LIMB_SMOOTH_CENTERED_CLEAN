# V110.3.19.2 · Soft Joint-Limit Warnings + Consistent Gate

## Corrección
- Restaura la puerta por modalidad validada en V110.3.11/V110.3.12.
- En monocular y biplanar 3D estimado, la Z inferida/estimada sigue siendo informativa y no bloqueante.
- Un único DoF no crítico en límite (cabeza, escápula, hombro, codo, muñeca, tobillo/pie) se muestra como **warning**, no como FAIL.
- Límites críticos de cadera o rodilla siguen siendo bloqueantes.
- Tres o más límites simultáneos se consideran saturación general y siguen provocando FAIL.
- En 3D calibrado se mantiene auditoría estricta: XY, Z y todos los límites son bloqueantes.
- Los avisos blandos se muestran explícitamente en el Frame 1 y en la puerta de propagación.

## Conservado
- SKEL24 y Unified Coordinate Frame.
- Sexo inmediato de V110.3.19.1.
- Migración/reproducción NPZ.
- Descarga de vídeos, incluido vídeo de malla SKEL.
- Correcciones temporales de miembros inferiores y Pose-Sequence Integrity.
- B2/cache y fallback manual.
