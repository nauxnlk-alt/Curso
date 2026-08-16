def busqueda_lineal(lista, objetivo):
    comparaciones = 0
    for i in range(len(lista)):
        comparaciones += 1
        if lista[i] == objetivo:
            return i, comparaciones
    return -1, comparaciones

def busqueda_binaria(lista, objetivo):
    izquierda = 0
    derecha = len(lista) - 1
    comparaciones = 0

    while izquierda <= derecha:
        medio = (izquierda + derecha) // 2
        comparaciones += 1

        if lista[medio] == objetivo:
            return medio, comparaciones
        elif lista[medio] < objetivo:
            izquierda = medio + 1
        else:
            derecha = medio - 1

    return -1, comparaciones

# Datos de prueba
datos = list(range(1, 200001))
objetivo = 175432

# Búsqueda lineal
inicio = time.perf_counter()
pos1, comp1 = busqueda_lineal(datos, objetivo)
tiempo1 = time.perf_counter() - inicio

# Búsqueda binaria
inicio = time.perf_counter()
pos2, comp2 = busqueda_binaria(datos, objetivo)
tiempo2 = time.perf_counter() - inicio

print("BUSQUEDA LINEAL")
print("Posicion:", pos1)
print("Comparaciones:", comp1)
print("Tiempo:", tiempo1, "segundos")

print("\nBUSQUEDA BINARIA")
print("Posicion:", pos2)
print("Comparaciones:", comp2)
print("Tiempo:", tiempo2, "segundos")
