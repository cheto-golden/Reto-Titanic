# Reto: Titanic - Machine Learning from Disaster
<p align="center">
  <img src="Image/titanic.png" alt="Titanic Disaster">
</p>

## Equipo 5
### Integrantes de equipo:
- [María Lynne Camacho Padilla](mailto:a01423135@tec.mx)
- [Emiliano Ferreira Guadarrama](mailto:a01654418@tec.mx)
- [Humberto Alejandro Rosas Téllez](mailto:a01659823@tec.mx)
- [Victoria Estefanía Vázquez Morales](mailto:a01654095@tec.mx)  
## Propuesta de solución resumida
Nuestra propuesta comienza con el preprocesamiento de los datos, donde tomamos las siguientes características: clase del pasajero, edad del pasajero cantidad de hermanos y cónyuges a bordo, cantidad de padres/madres e hijos a bordo, tarifa pagada por el boleto, sexo del pasajero, puerto de embarcación
Primero se discretiza la columna de Sex de manera que cada valor corresponda a un entero.
También se utiliza One Hot Encoding para separar la característica 'Embarked' en características dummies.
Para lidiar con los datos faltantes recomendamos imputar utilizando el algoritmo KNN con parámetro k=4.
Finalmente recomendamos realizar una estandarización de puntuación z a los datos.
Terminado este preprocesamiento proponemos un modelo Random Forest con parámetros:
- 100 árboles
- criterio de división: Gini
- mínimo de observaciones por división: 2
- mínimo de observaciones por hoja: 2
  
## Problemas y soluciones
### 1. Exploración
| Problema | Solución |
| :--: | :--: |
| Encontrar features que tuvieran valor para entrenar el modelo | Investigamos datos generes del dataset Titanic, basándonos en hechos históricos sobre cómo se decidió el abordaje los botes, según su clase, edad y sexo. También hicimos una matriz de correlación para comprobar que las features tuvieran alta relación |
| Crear nuevas features de valor | Creamos nuevas columnas basándonos en el pronombre de los pasajeros, y encontramos que Miss y Mrs sobrevivieron más que los demás, también creamos una columna del tamaño de las familias, así nos dimos cuenta de que las familias de 4 tenían más probabilidad de sobrevivir |
| Tratar con datos vacíos | Eliminamos las columnas que tenían muchos datos vacíos, como Cabin |
### 2. Pre procesamiento 
| Problema | Solución |
| :--: | :--: |
| Columnas poco relevantes | Se tomó la decisión de eliminar las columnas de PassengerId, Name, Cabin y Ticket; debido a que, según el análisis de correlación, no influían lo suficiente para determinar si alguien sobrevivió o no |
| Columnas categóricas | Se discretizó la columna de Sex, para que fuese 0 y 1. También la columna de Embarked tenía tres categorías: Q, C, S; según el puerto desde donde subió el pasajero al Titanic, por lo que se agregaron 3 columnas adicionales, una por cada categoría, con One Hot Encoder. |
| Imputación de datos | Se utilizó KNN imputer para imputar datos en la columna de Age. El k seleccionado fue 4, debido a que tuvo una distribución más acercada a la real de los datos existentes. |
|Estandarización| Se realizó la estandarización de todos los datos en el _dataframe_, para tener todos los valores en una misma escala.  
### 3. Selección de modelo 
Con la finalidad de tratar de obtener la mayor exactitud y precisión en la predicción de las personas que sobrevivieron o no al desastre en el Titanic, se seleccionaron tres distintos modelos de Machine Learning para realizar esta clasificación, los cuales se describen a continuación:

| Modelo | Justificación de uso |
| :--: | :--: |
| Random Forest Classifier | útil cuando se tiene la presencia de valores faltantes y categóricos, además de, tener una gran capacidad para el manejo de clasificaciones binarias y de ser robusto ante el overfitting. |
| SVM Kernel RBF | resistente frente a los Outliers y de gran utilidad cuando se tiene datos no linealmente separables (modelos no lineales). |
| KNeighborsClassifier| es simple de implementar, no requiere parámetros como otros modelos y permite un control entre el balanceo entre el sesgo y varianza que pudieran tener los datos debido a que se puede ajustar el número de vecinos (su complejidad) |
### 4. Resultados 
| Problema | Solución |
| :--: | :--: |
| Posibles datos con _overfitting_ en nuestro mejor modelo: Random Forest | En las métricas se notó que podría existir un _overfitting_ de los datos en Random Forest, pero al ser un modelo flexible pudimos confiar en la solución |
#### Link al Colab (solo profesores):
[Reto_Titanic_Eq_5.ipynb](https://colab.research.google.com/drive/1Nw_dUGjtbyqSekWWKl9ucUqSrzp3orcj?usp=sharing)

#### [Ver la presentación del proyecto](E5_RetoTitanic.pdf)
