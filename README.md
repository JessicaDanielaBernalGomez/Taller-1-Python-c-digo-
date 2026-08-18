# Taller 1 Python (código)
E.P.1 Algoritmos de Robótica

## A. Sin interacción de consola

**1.** Realice un programa que sume, reste, multiplique (producto punto y producto cruz) y divida dos vectores previamente inicializados.

### Solución (Código)

```python
import numpy as np

# Vectores
vector_A = np.array([2, 4, 6])
vector_B = np.array([1, 3, 5])

# Suma
suma = vector_A + vector_B

# Resta
resta = vector_A - vector_B

# Producto punto
producto_punto = np.dot(vector_A, vector_B)

# Producto cruz
producto_cruz = np.cross(vector_A, vector_B)

# División
division = vector_A / vector_B

# Resultados
print("Vector A:", vector_A)
print("Vector B:", vector_B)
print("Suma:", suma)
print("Resta:", resta)
print("Producto punto:", producto_punto)
print("Producto cruz:", producto_cruz)
print("División:", division)
```

**2.** Realice un programa que sume, reste, multiplique (producto punto y producto cruz) y divida dos matrices previamente inicializadas.

### Solución (Código)

```python
import numpy as np

# Matrices 
matriz_A = np.array([
    [2, 4],
    [6, 8]
])

matriz_B = np.array([
    [1, 3],
    [5, 7]
])

# Suma
suma = matriz_A + matriz_B

# Resta
resta = matriz_A - matriz_B

# Producto punto
producto_punto = np.dot(matriz_A, matriz_B)

# Producto cruz
producto_cruz = np.cross(matriz_A, matriz_B)

# División
division = matriz_A / matriz_B

# Resultados
print("Matriz A:", matriz_A)
print("Matriz B:", matriz_B)
print("Suma:", suma)
print("Resta:", resta)
print("Producto punto:", producto_punto)
print("Producto cruz:", producto_cruz)
print("División:", division)
```

**3.** Realice un programa que convierta coordenadas rectangulares a cilíndricas y esféricas, para lo cual deben consultar sobre el uso de funciones trigonométricas en Python. 

### Solución (Código)

```python
import numpy as np

# Coordenadas rectangulares
x = 3
y = 4
z = 5

# Conversión a coordenadas cilíndricas

rho = np.sqrt(x**2 + y**2)
phi = np.arctan2(y, x)
z_cilindrica = z

# Convertir ángulo de radianes a grados
phi_grados = np.degrees(phi)

# Conversión a coordenadas esféricas

r = np.sqrt(x**2 + y**2 + z**2)

theta = np.arccos(z / r)
theta_grados = np.degrees(theta)

phi_esferica = np.arctan2(y, x)
phi_esferica_grados = np.degrees(phi_esferica)

# Resultados

print("Coordenadas rectangulares:")
print("x =", x)
print("y =", y)
print("z =", z)

print("\nCoordenadas cilíndricas:")
print("rho =", rho)
print("phi =", phi_grados, "grados")
print("z =", z_cilindrica)

print("\nCoordenadas esféricas:")
print("r =", r)
print("theta =", theta_grados, "grados")
print("phi =", phi_esferica_grados, "grados")
```

**4.** Realice un programa para el cálculo de la resistencia de una RTD de platino (PT100) en función de la temperatura.

### Solución (Código)

```python
import numpy as np

# Parámetros de la PT100
R0 = 100
A = 3.9083e-3
B = -5.775e-7
temperatura = 100

# Cálculo de la resistencia
resistencia = R0 * (1 + A * temperatura + B * temperatura**2)

# Mostrar resultado
print("Sensor RTD PT100")
print("Temperatura:", temperatura, "°C")
print("Resistencia:", resistencia, "Ω")
```

**5.** Realice en funciones las rotaciones en X, Y y Z, donde se tenga un parámetro de entrada (ángulo) y un parámetro de salida (matriz).

### Solución (Código)

```python
import numpy as np

# Rotación alrededor del eje X
def rotacion_x(angulo):
    angulo_rad = np.radians(angulo)

    matriz = np.array([
        [1, 0, 0],
        [0, np.cos(angulo_rad), -np.sin(angulo_rad)],
        [0, np.sin(angulo_rad), np.cos(angulo_rad)]
    ])

    return matriz

# Rotación alrededor del eje Y
def rotacion_y(angulo):
    angulo_rad = np.radians(angulo)

    matriz = np.array([
        [np.cos(angulo_rad), 0, np.sin(angulo_rad)],
        [0, 1, 0],
        [-np.sin(angulo_rad), 0, np.cos(angulo_rad)]
    ])

    return matriz

# Rotación alrededor del eje Z
def rotacion_z(angulo):
    angulo_rad = np.radians(angulo)

    matriz = np.array([
        [np.cos(angulo_rad), -np.sin(angulo_rad), 0],
        [np.sin(angulo_rad), np.cos(angulo_rad), 0],
        [0, 0, 1]
    ])

    return matriz

# Ángulo definido
angulo = 45

# Obtener matrices
Rx = rotacion_x(angulo)
Ry = rotacion_y(angulo)
Rz = rotacion_z(angulo)

# Resultados
print("Ángulo:", angulo, "grados")

print("\nMatriz de rotación X:")
print(Rx)

print("\nMatriz de rotación Y:")
print(Ry)

print("\nMatriz de rotación Z:")
print(Rz)
```

**6.** Realice un programa que calcule la fuerza de avance y retroceso de un cilindro neumático de doble efecto. Debe establecer previamente los valores de presión, así como las dimensiones físicas del cilindro para realizar el cálculo.

### Solución (Código)

```python
import numpy as np

# Datos cilindro neumático doble efecto

presion_bar = 6
diametro_cilindro_mm = 50
diametro_vastago_mm = 20

# Conversión de unidades
presion_pa = presion_bar * 100000
diametro_cilindro_m = diametro_cilindro_mm / 1000
diametro_vastago_m = diametro_vastago_mm / 1000

# Área del pistón
area_piston = (np.pi * diametro_cilindro_m**2) / 4

# Área del vástago
area_vastago = (np.pi * diametro_vastago_m**2) / 4

# Fuerza de avance
fuerza_avance = presion_pa * area_piston

# Fuerza de retroceso
area_retroceso = area_piston - area_vastago
fuerza_retroceso = presion_pa * area_retroceso

# Resultados
print("CILINDRO NEUMÁTICO DE DOBLE EFECTO")
print("Presión:", presion_bar, "bar")
print("Diámetro del cilindro:", diametro_cilindro_mm, "mm")
print("Diámetro del vástago:", diametro_vastago_mm, "mm")

print("\nFuerza de avance:", fuerza_avance, "N")
print("Fuerza de retroceso:", fuerza_retroceso, "N")
```
