## Proyecto final del prework - Solución paso a paso

## ¡Empecemos a resolver los ejercicios!

**Ejercicio 00: Declaraciones básicas**
```python
# Tu nombre, como cadena de texto
name = "Tu Nombre"

# Tu edad, como entero
age = 30

# ¿Te gusta programar? Como booleano
likes_programming = True

# Tu promedio de calificaciones, como decimal
average_grade = 8.5

# Lista de números favoritos
favorite_numbers = [3, 7, 11, 13, 17]

# Información del estudiante como diccionario
student = {
  "nombre": "Alicia",
  "edad": 22,
  "calificacion_final": 9.2
}
```


**Ejercicio 01: Análisis básico de datos**
```python

# Lista de calificaciones
calificaciones = [8.5, 9.2, 7.8, 8.9, 10]

# Calcular promedio
promedio = sum(calificaciones) / len(calificaciones)
print("Promedio de calificaciones:", promedio)

# Encontrar la calificación más alta y la más baja
calificacion_mas_alta = max(calificaciones)
calificacion_mas_baja = min(calificaciones)
print("Calificación más alta:", calificacion_mas_alta)
print("Calificación más baja:", calificacion_mas_baja)
```
### Limpieza de datos inmobiliarios con Pandas para un análisis eficiente

**Ejemplo: Cargar y explorar el conjunto de datos**
```python
import pandas as pd

# Carga los datos CSV
df = pd.read_csv('assets/real_estate.csv', sep=';')

# Muestra las primeras 5 filas
print(df.head())
```

**Ejercicio 01: ¿Cuál es la casa más cara de todo el conjunto de datos?**
```python
# Encuentra la casa más cara
casa_mas_cara = df.loc[df['price'].idxmax()]
print("La casa más cara se encuentra en", casa_mas_cara['url_inmueble'], "y su precio es", casa_mas_cara['price'])
```

**Ejercicio 02: ¿Cuál es la casa más barata del conjunto de datos?**
```python
# Encuentra la casa más barata
casa_mas_barata = df.loc[df['price'].idxmin()]

# Imprime la dirección y el precio
print("La casa más barata se encuentra en", casa_mas_barata['url_inmueble'], "y su precio es", casa_mas_barata['price'])
```

**Ejercicio 03: ¿Cuál es la casa más grande y la más pequeña del conjunto de datos?**
```python
# Encuentra la casa más grande por superficie
casa_mas_grande = df.loc[df['surface'].idxmax()] 

# Encuentra la casa más pequeña por superficie
casa_mas_pequena = df.loc[df['surface'].idxmin()]

# Imprime los resultados
print("La casa más grande se encuentra en", casa_mas_grande['url_inmueble'], "y su superficie es de", casa_mas_grande['surface'], "metros cuadrados.")
print("La casa más pequeña se encuentra en", casa_mas_pequena['url_inmueble'], "y su superficie es de", casa_mas_pequena['surface'], "metros cuadrados.") 
```

**Ejercicio 04: ¿Cuántas poblaciones únicas hay en el conjunto de datos?**
```python
# Encuentra poblaciones únicas
poblaciones_unicas = df['level5'].unique()

# Cuenta el número de poblaciones únicas
numero_poblaciones = len(poblaciones_unicas)

# Imprime el número de poblaciones únicas
print("Número de poblaciones únicas:", numero_poblaciones)

# Imprime los nombres de las poblaciones
print("Poblaciones:", ", ".join(poblaciones_unicas))
```

**Ejercicio 05: ¿El conjunto de datos contiene valores nulos (NA)?**
```python
# Verifica si hay valores nulos en todo el DataFrame
tiene_valores_nulos = df.isnull().any().any() 

# Encuentra columnas con valores nulos
columnas_con_nulos = df.columns[df.isnull().any()]

# Imprime los resultados
print("El conjunto de datos contiene valores nulos:", tiene_valores_nulos)
print("Columnas con valores nulos:", columnas_con_nulos.tolist()) 
```

**Ejercicio 06: Eliminar los valores nulos (NA) del conjunto de datos, si es aplicable**
```python
# Tamaño original del DataFrame
original_size = df.shape

# Eliminar filas con cualquier valor nulo
df_cleaned = df.dropna() 

# Tamaño del DataFrame después de la limpieza
cleaned_size = df_cleaned.shape

# Comparar tamaños
print("Tamaño original del DataFrame:", original_size)
print("Tamaño del DataFrame limpio:", cleaned_size)
print("Número de filas eliminadas:", original_size[0] - cleaned_size[0]) 
```

**Ejercicio 07: ¿Cuál es el precio promedio en la población de "Arroyomolinos (Madrid)"?**
```python
# Filtrar el DataFrame para la población especificada
arroyomolinos_df = df[df['level5'] == 'Arroyomolinos (Madrid)'] 

# Calcular el precio promedio
precio_promedio_arroyomolinos = arroyomolinos_df['price'].mean()

# Imprimir el precio promedio
print("Precio promedio en Arroyomolinos (Madrid):", precio_promedio_arroyomolinos)  
```


**Ejercicio 08: Graficar el histograma de precios para la población de "Arroyomolinos (Madrid)" y explicar lo observado**
```python
import matplotlib.pyplot as plt

# Crear un histograma de precios para Arroyomolinos (Madrid)
plt.hist(arroyomolinos_df['price'], bins=20) 
plt.xlabel("Precio")
plt.ylabel("Frecuencia")
plt.title("Histograma de Precios en Arroyomolinos (Madrid)")
plt.show() 

# Breve análisis del gráfico
print("El histograma muestra la distribución de los precios de las casas en Arroyomolinos (Madrid). \n" 
      "Se observa una distribución sesgada hacia la derecha, lo que indica que hay más casas con precios más bajos y menos con precios muy altos.") 
```