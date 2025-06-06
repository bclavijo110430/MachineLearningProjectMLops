# Predicción del Futuro de Empleados

## Caso de uso 
En un equipo de ciencia de datos, es común intentar encontrar continuamente un modelo mejor que el existente en producción. Es importante asegurarse de que el servicio no falle cuando se despliega el nuevo modelo.

Este proyecto demuestra cómo usar DagsHub y GitHub Actions para:
- probar automáticamente una pull request de un miembro del equipo
- fusionar una pull request cuando todas las pruebas han pasado
- desplegar el modelo de ML al servicio existente

![](https://cdn-images-1.medium.com/max/800/1*VZLOx6sCq9_Dj1-44mxKOQ.png)

Aquí está el resumen del flujo de trabajo:

## Experimentar en DagsHub
Después de experimentar con diferentes parámetros usando [MLFlow](https://mlflow.org/) y [DagsHub](https://towardsdatascience.com/dagshub-a-github-supplement-for-data-scientists-and-ml-engineers-9ecaf49cc505), elegimos una combinación de parámetros que ofrece un mejor rendimiento que el modelo existente en producción y se realiza el commit del código en Git.

![](https://cdn-images-1.medium.com/max/800/1*AVtGMnz8_2K3dOtQAKCTdQ.png)

## Usar GitHub Actions para Probar el Modelo
El primer flujo de trabajo llamado [test_model.yaml](https://github.com/khuyentran1401/employee-future-prediction/blob/master/.github/workflows/test_model.yaml) prueba automáticamente una nueva pull request, la cual solo puede fusionarse si todas las pruebas pasan.

![](https://cdn-images-1.medium.com/max/800/1*Prnyik5wQ2A5ciZP2NmRhw.png)

## Usar GitHub Actions para Desplegar el Modelo Después de la Fusión
El segundo flujo de trabajo llamado [deploy_app.yaml](https://github.com/khuyentran1401/employee-future-prediction/blob/master/.github/workflows/deploy_app.yaml) despliega automáticamente el nuevo modelo al servicio existente después de que la pull request es fusionada.

![](https://cdn-images-1.medium.com/max/800/1*gb37ASDRRILsKJYe3CBFyw.png).
