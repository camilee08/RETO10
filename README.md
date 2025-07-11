# RETO10
## 1. Desarrolle un programa que permita realizar la suma/resta de matrices. El programa debe validar las condiciones necesarias para ejecutar la operación.
Sabiendo que según https://es.wikipedia.org/wiki/Adici%C3%B3n_matricial la adición matricial es:
<img width="546" height="140" alt="Captura" src="https://github.com/user-attachments/assets/2177f782-40de-409a-9b20-5fdb1eed8656" />  
entonces el programa debe pedir al usuario dos matrices, elegir si quiere sumarlas o restarlas, verificar que tengan el mismo número de filas y columnas, hacer la suma o resta elemento por elemento e imprimir el resultado en forma de matriz.
```
# Función para imprimir la matriz
def impmatriz(matriz):
    for f in matriz:
        print(f)

# Función para pedir los datos de una matriz
def ingmatriz(filas, columnas, nombre):
    matriz = []
    print("Ingrese los datos para la matriz", nombre)
    for n in range(filas):
        fila = []
        for i in range(columnas):
            print("Elemento en la fila", n + 1, ", y en la columna", i + 1, ": ")
            valor = float(input())
            fila.append(valor)
        matriz.append(fila)
    return matriz

# Función para sumarlas
def sumarmatrices(A, B):
    resultado = []
    for i in range(len(A)):
        fila_resultado = []
        for j in range(len(A[i])):
            fila_resultado.append(A[i][j] + B[i][j])
        resultado.append(fila_resultado)
    return resultado

# Función para restarlas
def restar_matrices(A, B):
    resultado = []
    for n in range(len(A)):
        fila_resultado = []
        for i in range(len(A[n])):
            fila_resultado.append(A[n][i] - B[n][i])
        resultado.append(fila_resultado)
    return resultado

# Función principal
if __name__ == "__main__":
    filas = int(input("Ingrese el número de filas: ")) # Para tener más control de las otras funciones
    columnas = int(input("Ingrese el número de columnas: "))

    matriz_A = ingmatriz(filas, columnas, "A") # Se llaman la función anterior pero con su respectivo nombre
    matriz_B = ingmatriz(filas, columnas, "B")

    print("¿Qué operación desea realizar?") # Para que se ejecute la operación deseada
    print("sumar")
    print("restar")
    opcion = input("Eliga sumar o restar: ")

    if opcion == "sumar":
        resultado = sumarmatrices(matriz_A, matriz_B)
        print("Resultado:")
        impmatriz(resultado)
    elif opcion == "restar":
        resultado = restar_matrices(matriz_A, matriz_B)
        print("Resultado de la resta:")
        impmatriz(resultado)
```
## 2. Desarrolle un programa que permita realizar el producto de matrices. El programa debe validar las condiciones necesarias para ejecutar la operación.
Si según https://es.wikipedia.org/wiki/Multiplicaci%C3%B3n_de_matrices la multiplicación de dos matrices es 
<img width="556" height="224" alt="Captura" src="https://github.com/user-attachments/assets/b1b2c543-a0f5-469b-9966-b3e386ccc954" />  
y que Si A es de tamaño m x n, y B es de tamaño n x p, entonces su producto será una matriz de tamaño m x p. Entonces debe validar que el número de columnas de una matriz, en este caso A sea igual a filas de la otra matriz, B:
```
# Función para imprimir una matriz
def impmatriz(matriz):
    for f in matriz:
        print(f)

# Función para ingresar una matriz
def ingmatriz(filas, columnas, nombre):
    matriz = []
    print("Ingrese los datos para la matriz", nombre)
    for n in range(filas):
        fila = []
        for i in range(columnas):
            print("Elemento en la fila", n + 1, ", y en la columna", i + 1, ": ")
            valor = float(input())
            fila.append(valor)
        matriz.append(fila)
    return matriz

# Función para multiplicar las matrices
def multmatrices(A, B):
    filas_A = len(A)
    columnas_A = len(A[0])
    columnas_B = len(B[0]) # el resultado tiene que tener ese número de columnas
    resultado = []

    for n in range(filas_A):
        fila_resultado = []
        for i in range(columnas_B):
            suma = 0
            for j in range(columnas_A):
                suma += A[n][j] * B[j][i] #elemento de la fila n de A por elemento de la columna i de B
            fila_resultado.append(suma)
        resultado.append(fila_resultado)

    return resultado

# Función principal
if __name__ == "__main__":
    print("Ingrese dimensiones de la matriz A:")
    filas_A = int(input("Filas de A: "))
    columnas_A = int(input("Columnas de A: "))

    print("Ingrese dimensiones de la matriz B:")
    filas_B = int(input("Filas de B: "))
    columnas_B = int(input("Columnas de B: "))

    # Validar las condiciones para hacer la multiplicacion 
    if columnas_A != filas_B:
        print("No se puede multiplicar")
    else:
        A = ingmatriz(filas_A, columnas_A, "A")
        B = ingmatriz(filas_B, columnas_B, "B")
        resultado = multmatrices(A, B)
        print("Resultado es:")
        impmatriz(resultado)
```
## 3, Desarrolle un programa que permita obtener la matriz transpuesta de una matriz ingresada. El programa debe validar las condiciones necesarias para ejecutar la operación.
Una matriz transpuesta es la que se obtiene cuando se cambian las filas por las columnas, este tipo de operación no tiene reestricciones.
```
# Función para imprimir una matriz
def impmatriz(matriz):
    for f in matriz:
        print(f)

# Función para pedir los datos de una matriz
def ingmatriz(filas, columnas):
    matriz = []
    print("Ingrese los elementos de la matriz:")
    for n in range(filas):
        fila = []
        for j in range(columnas):
            print("Elemento en la fila", n + 1, "y columna", j + 1, ":")
            valor = float(input())
            fila.append(valor)
        matriz.append(fila)
    return matriz

# Función para calcular la matriz transpuesta
def transpuesta(matriz):
    filas = len(matriz)
    columnas = len(matriz[0])
    resultado = []
    for n in range(columnas):  # columnas se vuelven filas
        nueva_fila = []
        for i in range(filas):  # filas se vuelven columnas
            nueva_fila.append(matriz[i][n])
        resultado.append(nueva_fila)
    return resultado

# Función principal
if __name__ == "__main__":
    filas = int(input("Ingrese el número de filas: "))
    columnas = int(input("Ingrese el número de columnas: "))

    matriz = ingmatriz(filas, columnas)

    matriz_transpuesta = transpuesta(matriz)

    print("Matriz transpuesta:")
    impmatriz(matriz_transpuesta)
```
## 4. Desarrollar un programa que sume los elementos de una columna dada de una matriz.
