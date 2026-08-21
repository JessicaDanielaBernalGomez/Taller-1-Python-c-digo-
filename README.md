# Taller 1 Python (código)
E.P.1 Algoritmos de Robótica

## Integrantes:

Jessica Daniela Bernal Gómez - 120093

Jorman Santiago Preciado Duque - 122828

Danilo Rodriguez Malago - 119238

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
C = -4.183e-12
temperatura = -50

def resistencia_pt100(temperatura):

    # Rango: temperatura mayor o igual a 0 °C
    if temperatura >= 0:

        resistencia = R0 * (
            1 + A * temperatura + B * temperatura**2
        )

    # Rango: temperatura menor a 0 °C
    else:

        resistencia = R0 * (
            1
            + A * temperatura
            + B * temperatura**2
            + C * (temperatura - 100) * temperatura**3
        )

    return resistencia

# Cálculo de la resistencia
resistencia = resistencia_pt100(temperatura)

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

## B. Con interacción de consola (fprintf o disp) y teclado (input)

**1.** Realice un programa que calcule la potencia que consume un circuito ingresando por teclado el valor de corriente y voltaje.

### Solución (Código)

```python
print('Ingresa los valores de voltaje y corriente para calcular la potencia que consume un circuito')
voltaje = float(input("Ingrese el valor de voltaje(V) \n") )
corriente = float(input("Ingrese el valor de corriente(A) \n"))
Potencia=voltaje*corriente
print(f'La potencia con los valores ingresados es: {Potencia} w')
```

**2.** Realice un programa que calcule X números aleatorios en un rango determinado por el usuario.

### Solución (Código)

```python
import random
print("Generador numeros aleatorios")
cantidad = int(input("¿Cuantos numeros desea generar?: "))
minimo = int(input("Ingrese el valor minimo del rango: "))
maximo = int(input("Ingrese el valor maximo del rango: "))
numeros=[]
for i in range(cantidad):
    numero=random.randint(minimo,maximo)
    numeros.append(numero)

print("Los numero generados en los rangos dados son:\n")
print(numeros)
```

**3.** Realice un programa para el cálculo de volúmenes (Prisma, Pirámide, Cono truncado, Cilindro) donde el usuario pueda seleccionar el sólido y los parámetros de cada volumen. 

### Solución (Código)

```python
import math

print("Seleccione el solido al cual desea saber el volumen")
print("1. Prisma\n2. Piramida\n3 Cono truncado\n4.Cilindro\n")
Solido=int(input("Seleccione el solido:\n"))

if Solido == 1:
    print("PRISMA")
    area_base = float(input("Ingrese el area de la base: "))
    altura = float(input("Ingrese la altura: "))
    volumen = area_base * altura
    print(f"El volumen del prisma es: {volumen}")
elif Solido == 2:
    print("PIRAMIDE")
    area_base = float(input("Ingrese el area de la base: "))
    altura = float(input("Ingrese la altura: "))
    volumen = (area_base * altura) / 3
    print(f"El volumen de la piramide es: {volumen}")
elif Solido == 3:
    print("CONO TRUNCADO")
    radio_mayor = float(input("Ingrese el radio mayor: "))
    radio_menor = float(input("Ingrese el radio menor: "))
    altura = float(input("Ingrese la altura: "))
    volumen = (math.pi * altura / 3) * (radio_mayor*2+radio_mayor*radio_menor+radio_menor*2)
    print(f"El volumen del cono truncado es: {volumen}")
elif Solido == 4:
    print("CILINDRO")
    radio = float(input("Ingrese el radio: "))
    altura = float(input("Ingrese la altura: "))
    volumen = math.pi * radio**2 * altura
    print(f"El volumen del cilindro es: {volumen}")
else :
    print("Opcion invalida")
```

**4.** Realice un programa que le permita al usuario escoger entre robot Cilíndrico, Cartesiano y esférico, donde como respuesta a la selección conteste con el tipo y número de articulaciones que posee.

### Solución (Código)

```python
print("Escoger entre robot Cilíndrico, Cartesiano y esférico:")
print("1. Robot Cilindrico\n2. Robot Cartesiano\n3. Robot Esferico")

Robot = int(input("Seleccione el tipo de robot: "))

if Robot == 1:
    print("\nRobot seleccionado: Cilindrico")
    print("Numero de articulaciones: 3")
    print("2 articulaciones prismaticas y 1 rotacional.")
elif Robot == 2:
    print("\nRobot seleccionado: Cartesiano")
    print("Numero de articulaciones: 3")
    print("3 articulaciones prismaticas.")
elif Robot == 3:
    print("\nRobot seleccionado: Esferico")
    print("Numero de articulaciones: 3")
    print("2 articulaciones rotacionales y 1 prismatica.")
else:
    print("Opcion invalida.")
```

**5.** Escribir un programa que realice la pregunta ¿Desea continuar Si/No? y que no deje de hacerla hasta que el usuario teclee No.

### Solución (Código)

```python
while True:
    res = input("¿Desea continuar Si/No? ")
    res = res.lower()
    if res == "si":
        print("El programa continua\n")
    elif res == "no":
        print("Programa finalizado")
        break
    else:
        print("Respuesta no valida. Escriba Si o No.\n")
```

## C.  Uso de las funciones para graficar

**1.** Realice un programa que grafique el comportamiento de un sensor PT100 desde -200°C a 200°C.

### Solución (Código)

```python
import numpy as np
import matplotlib.pyplot as plt

R0 = 100
A = 3.9083e-3
B = -5.775e-7
C = -4.183e-12

T = np.linspace(-200, 200, 1000)

R = []

for temperatura in T:
    if temperatura >= 0:
        resistencia = R0 * (
            1 + A * temperatura + B * temperatura**2
        )
    else:
        resistencia = R0 * (
            1
            + A * temperatura
            + B * temperatura**2
            + C * (temperatura - 100) * temperatura**3
        )

    R.append(resistencia)

plt.figure(figsize=(9, 5))
plt.plot(T, R)

plt.title("Comportamiento de un sensor PT100")
plt.xlabel("Temperatura (°C)")
plt.ylabel("Resistencia (Ohm)")
plt.grid(True)

plt.show()
```

**2.** Realice un programa que le permita al usuario ingresar los coeficientes de una función de transferencia de segundo orden y graficar su comportamiento, además se debe mostrar que tipo de sistema es: subamortiguado, criticamente amortiguado y sobreamortiguado.

### Solución (Código)

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import signal

print("FUNCIÓN DE TRANSFERENCIA DE SEGUNDO ORDEN")

K = float(input("Ingrese la ganancia K: "))
a1 = float(input("Ingrese el coeficiente de s: "))
a0 = float(input("Ingrese Factor de amortiguamiento: "))

numerador = [K]
denominador = [1, a1, a0]

sistema = signal.TransferFunction(numerador, denominador)

# Polos
polos = np.roots(denominador)

print("\nPolos del sistema:")
print(polos)

# Determinar tipo de sistema
discriminante = a1**2 - 4*a0

if discriminante < 0:
    tipo = "SUBAMORTIGUADO"
elif discriminante == 0:
    tipo = "CRÍTICAMENTE AMORTIGUADO"
else:
    tipo = "SOBREAMORTIGUADO"

print("\nTipo de sistema:", tipo)

# Respuesta al escalón
tiempo, respuesta = signal.step(sistema)

plt.figure(figsize=(9, 5))
plt.plot(tiempo, respuesta)

plt.title("Respuesta al escalón - " + tipo)
plt.xlabel("Tiempo (s)")
plt.ylabel("Amplitud")
plt.grid(True)

plt.show()
```

**3.** Implemente la ecuación de carga y descarga para un circuito RC. El usuario ingresa por teclado el valor de voltaje (V), capacitancia (𝜇𝐹) y resistencia (Ω). Posteriormente realice en Python la gráfica.

### Solución (Código)

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import signal

print("FUNCIÓN DE TRANSFERENCIA DE SEGUNDO ORDEN")

K = float(input("Ingrese la ganancia K: "))
a1 = float(input("Ingrese el coeficiente de s: "))
a0 = float(input("Ingrese el término independiente: "))

# Función de transferencia
numerador = [K]
denominador = [1, a1, a0]

sistema = signal.TransferFunction(numerador, denominador)

# Polos
polos = np.roots(denominador)

print("\nPolos del sistema:")
print(polos)

# Determinar tipo de sistema
discriminante = a1**2 - 4*a0

if discriminante < 0:
    tipo = "SUBAMORTIGUADO"
elif discriminante == 0:
    tipo = "CRÍTICAMENTE AMORTIGUADO"
else:
    tipo = "SOBREAMORTIGUADO"

print("\nTipo de sistema:", tipo)

# Respuesta al escalón
tiempo, respuesta = signal.step(sistema)

plt.figure(figsize=(9, 5))
plt.plot(tiempo, respuesta)

plt.title("Respuesta al escalón - " + tipo)
plt.xlabel("Tiempo (s)")
plt.ylabel("Amplitud")
plt.grid(True)

plt.show()
```

**4.** Consulte y elabore un sistema coordenado X, Y y Z donde se dibuje un vector con coordenadas ingresadas por el usuario.

### Solución (Código)

```python
import numpy as np
import matplotlib.pyplot as plt

print("CIRCUITO RC - CARGA Y DESCARGA")

V = float(input("Ingrese el voltaje (V): "))
C_micro = float(input("Ingrese la capacitancia (uF): "))
R = float(input("Ingrese la resistencia (ohm): "))

# Convertir microfaradios a faradios
C = C_micro * 1e-6

# Constante de tiempo
tau = R * C

print("\nConstante de tiempo:")
print("Tau =", tau, "segundos")

# Tiempo de simulación
t = np.linspace(0, 5*tau, 1000)

# Carga
Vc_carga = V * (1 - np.exp(-t/tau))

# Descarga
Vc_descarga = V * np.exp(-t/tau)

# Gráfica
plt.figure(figsize=(9, 5))

plt.plot(t, Vc_carga, label="Carga")
plt.plot(t, Vc_descarga, label="Descarga")

plt.title("Carga y descarga de un circuito RC")
plt.xlabel("Tiempo (s)")
plt.ylabel("Voltaje del capacitor (V)")
plt.grid(True)
plt.legend()

plt.show()
```

**5.** Dibuje el nombre de cada uno de los integrantes del grupo en un plot en 2D, teniendo en cuenta líneas rectas y/o curvas.

### Solución (Código)

```python
import numpy as np
import matplotlib.pyplot as plt

plt.figure(figsize=(14, 8))

def dibujar_letra(letra, x, y):

    if letra == "D":
        plt.plot(
            [x, x, x + 0.6, x + 0.9, x + 0.6, x],
            [y, y + 2, y + 2, y + 1, y, y]
        )
    elif letra == "A":
        plt.plot(
            [x, x + 0.5, x + 1],
            [y, y + 2, y]
        )

        # Barra central
        plt.plot(
            [x + 0.2, x + 0.8],
            [y + 0.8, y + 0.8]
        )
    elif letra == "N":
        plt.plot(
            [x, x, x + 1, x + 1],
            [y, y + 2, y, y + 2]
        )
    elif letra == "I":
        plt.plot(
            [x, x + 1],
            [y + 2, y + 2]
        )

        plt.plot(
            [x + 0.5, x + 0.5],
            [y + 2, y]
        )

        plt.plot(
            [x, x + 1],
            [y, y]
        )

    elif letra == "L":
        plt.plot(
            [x, x],
            [y + 2, y]
        )

        plt.plot(
            [x, x + 1],
            [y, y]
        )

    elif letra == "O":

        theta = np.linspace(0, 2 * np.pi, 100)

        x_o = x + 0.5 + 0.5 * np.cos(theta)
        y_o = y + 1 + 1 * np.sin(theta)

        plt.plot(x_o, y_o)

    elif letra == "E":

        # Línea vertical
        plt.plot(
            [x, x],
            [y, y + 2]
        )

        # Línea superior
        plt.plot(
            [x, x + 1],
            [y + 2, y + 2]
        )

        # Línea central
        plt.plot(
            [x, x + 0.8],
            [y + 1, y + 1]
        )

        # Línea inferior
        plt.plot(
            [x, x + 1],
            [y, y]
        )

    elif letra == "J":

        # Línea superior
        plt.plot(
            [x, x + 1],
            [y + 2, y + 2]
        )

        # Línea vertical
        plt.plot(
            [x + 0.5, x + 0.5],
            [y + 2, y + 0.4]
        )

        # Parte curva
        theta = np.linspace(np.pi, 2 * np.pi, 50)

        x_j = x + 0.2 + 0.3 * np.cos(theta)
        y_j = y + 0.4 + 0.4 * np.sin(theta)

        plt.plot(x_j, y_j)

    elif letra == "R":

        # Línea vertical
        plt.plot(
            [x, x],
            [y, y + 2]
        )

        # Parte superior
        plt.plot(
            [x, x + 0.6, x + 0.8, x + 0.6, x],
            [y + 2, y + 2, y + 1.5, y + 1, y + 1]
        )

        # Diagonal
        plt.plot(
            [x + 0.5, x + 1],
            [y + 1, y]
        )

    elif letra == "M":

        plt.plot(
            [x, x, x + 0.5, x + 1, x + 1],
            [y, y + 2, y + 1, y + 2, y]
        )

def dibujar_nombre(nombre, x_inicial, y_inicial):

    espacio = 1.4

    for i, letra in enumerate(nombre):

        x = x_inicial + i * espacio

        dibujar_letra(letra, x, y_inicial)

dibujar_nombre("DANILO", 0, 5.5)

dibujar_nombre("DANIELA", 0, 2)

dibujar_nombre("JORMAN", 0, -1.5)

plt.title("Nombres de los integrantes")

plt.xlabel("Eje X")
plt.ylabel("Eje Y")

plt.axis("equal")

plt.grid(True)

plt.xlim(-1, 11)
plt.ylim(-2.5, 8)

plt.show()
```

**6.** Obtenga las coordenadas X y Y de los contornos de dos logos de automóviles (Chevrolet, Hyundai, Mazda, etc.), a través de Python.

![Logo Chevrolet](image.png)

![Logo Renault](image2.png)

### Solución (Código)

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
from google.colab import drive
drive.mount('/content/drive')

def obtener_contorno(ruta_imagen, nombre):

    img = cv2.imread(ruta_imagen)

    if img is None:
        print(f"No se pudo abrir: {ruta_imagen}")
        return None
    gris = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
    gris = cv2.GaussianBlur(gris, (5, 5), 0)
    _, binaria = cv2.threshold(
        gris,
        0,
        255,
        cv2.THRESH_BINARY_INV + cv2.THRESH_OTSU
    )
    contornos, jerarquia = cv2.findContours(
        binaria,
        cv2.RETR_EXTERNAL,
        cv2.CHAIN_APPROX_NONE
    )
    if len(contornos) == 0:
        print(f"No se encontraron contornos en {nombre}")
        return None
    contorno = max(contornos, key=cv2.contourArea)
    coordenadas = contorno.reshape(-1, 2)

    print(f"\n{nombre}")
    print("Número de puntos:", len(coordenadas))
    print("Primeras coordenadas X,Y:")
    print(coordenadas[:20])
    np.savetxt(
        f"{nombre}_coordenadas.csv",
        coordenadas,
        delimiter=",",
        header="X,Y",
        comments="",
        fmt="%d"
    )

    print(f"Archivo guardado: {nombre}_coordenadas.csv")

    alto, ancho = gris.shape

    imagen_contorno = np.zeros(
        (alto, ancho),
        dtype=np.uint8
    )
    cv2.drawContours(
        imagen_contorno,
        [contorno],
        -1,
        255,
        2
    )
    plt.figure(figsize=(8, 6))
    plt.imshow(imagen_contorno, cmap="gray")
    plt.title(f"Contorno - {nombre}")
    plt.axis("off")
    plt.show()

    return coordenadas

chevrolet = obtener_contorno(
    "/content/image.png",
    "Chevrolet"
)

renault = obtener_contorno(
    "/content/image2.png",
    "Renault"
)
```
