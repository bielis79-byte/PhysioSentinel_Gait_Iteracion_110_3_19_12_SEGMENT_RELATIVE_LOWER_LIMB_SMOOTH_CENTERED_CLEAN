# V110.3.19.2 · Soft Joint-Limit Warnings + Consistent Gate

Esta versión corrige una regresión de la puerta anatómica: un ajuste biplanar estimado con RMSE XY válido no debe quedar bloqueado únicamente porque un DoF periférico o de cabeza alcance su límite conservador.

La regla restaurada distingue entre adquisición no métrica y 3D calibrado. En monocular/biplanar estimado se priorizan XY, SKEL24, Unified Frame y límites críticos de cadera/rodilla. La profundidad Z estimada, los errores angulares dependientes de Z y los límites aislados no críticos se conservan como avisos. En 3D calibrado la auditoría sigue siendo estricta.
