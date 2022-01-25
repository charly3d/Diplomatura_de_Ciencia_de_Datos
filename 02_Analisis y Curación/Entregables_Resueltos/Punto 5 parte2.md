## Criterios de exclusión de ejemplos
  1. Se eliminaron ejemplos donde el precio fuera superior a 2.352.362,5 AUD
  2. Se eliminan ejemplos donde el año de construcción es previo a 1876
  3. Se eliminaron las filas dónde landsize es mayor a 1360.5
  4. Se eliminaron las filas dónde Building Area era mayor a 276
  5. Se Fija valor máximo de Rooms en 6, asignando este valor a las propiedades con más de 6, debido a la baja frecuencia de estos datos
  6. Se Fija valor máximo de Bathrooms en 4,asignando este valor a las propiedades con más de 4, debido a la baja frecuencia de estos datos
  7. Se Fija valor máximo de Bathrooms en 4,asignando este valor a las propiedades con más de 4, debido a la baja frecuencia de estos datos
  8. En la variable Bathroom Se asigno 1 a todas las propiedades en los que este valor era 0.
  9. En la variable Car Se asigno 0 a todas las propiedades en los que este valor era nan.
 10. En la variable Car Se Fija valor máximo de Bathrooms en 5,asignando este valor a las propiedades con más de 5, debido a la baja frecuencia de estos datos.

## Criterios de exclusión de variables
 1. Se elimina la columna Bedroom2, por su alta correlación con rooms, su dudosa procedencia y no aporte de nueva información
 2. Se elimina la columna Address, por se variable categorica de muchas categorias, existiendo otras variables de ubicación mejores.
 3. Se elimina la columna Distance, por su baja correlación con Price.
 4. Se elimina la columna Propertycount, por su baja correlación con Price.
 5. Se elimina la columna SellerG, por sus multiples valores posibles y porque el nombre del vendedor no nos parece relevante en la prediccion de precios
 6. Se elimina la columna Date, porque la serie de tiempo es Estacionaria.
 7. No se utiliza la columna CouncilArea, por sus más de 30 categorias que al intentar agrupar para que queden 15, la columna de otros se vuelve la más frecuente.
 8. No se utiliza la columna Suburb, por la misma razón que Council Area


## Características seleccionadas

### Características categóricas
  1. Type: tipo de propiedad. 3 valores posibles.
  2. Method: metodo de venta . 5 valores posibles.
  3. Regionname: nombre de la region donde se encuentra la propiedad.8 valores posibles.
  4. PostCode_agrupado: Se separo a los postcode agrupandolos en 8 categorias.Desde 3000 a 3999.
  5. Todas las características categóricas fueron codificadas con un
  método OneHotEncoding utilizando todos sus valores, ya que no superan los 24 valores en total
 
### Características numéricas
  1. Rooms: Cantidad de habitaciones
  2. Bathroom: Cantidad de Baños de la propiedad
  3. Car: Cantidad de espacios para los vehiculos
  4. Airbnb_Price: Se agrega el precio promedio diario de 
     publicaciones de la plataforma AirBnB en el mismo código 
     postal y en caso de no tener conicidecias se establecio un criterio de cuadricula
     pasando coordenadas en lat, long a utm y dividiendo la cuadricula en 20 x 20,dando como resultados cuadros de 4,824km por 4,198km-
 5.Landsize: el tamaño de la propiedad.
 6.Precio: Precio de la propiedad, No se usa para imputar valores, ni para el calculo de las componentes, ya que el fin de todo es poder predecir precios
 7.YearBuilt: Año de construcción de la propiedad
 8.BuildingArea: Superficie de la propiedad
 
### Transformaciones:
  1. Todas las características numéricas fueron escaladas
  2. Las columnas `YearBuilt` y `BuildingArea` fueron imputadas utilizando el 
     algoritmo KNN, con n=5 (La columna `Price` no fue utilizada)
  4.Luego para reducir la dimensionalidad con el metodo de PCA, se realizo una estandarización (La columna `Price` no fue utilizada)
 
### Datos aumentados
  1. Se agregan las 5 primeras columnas obtenidas a través del
     método de PCA, aplicado sobre el conjunto de datos
     totalmente procesado.(La columna `Price` no fue utilizada)