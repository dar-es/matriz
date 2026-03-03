import numpy as np

def generar_gran_matriz(nombre_archivo, filas, columnas, chunk_size=1000):
    """Genera una matriz binaria y la guarda en formato binario (.npy)"""
    # Creamos un archivo en disco usando memory mapping para no cargar todo en RAM
    fp = np.memmap(nombre_archivo, dtype='int8', mode='w+', shape=(filas, columnas))
    
    for i in range(0, filas, chunk_size):
        end = min(i + chunk_size, filas)
        # Generamos entradas aleatorias de 0 y 1 para este bloque
        fp[i:end, :] = np.random.randint(0, 2, size=(end - i, columnas), dtype='int8')
        print(f"Procesando filas: {i} a {end}...")
    
    # Limpiar memoria
    del fp
    print(f"¡Hecho! Archivo guardado como {nombre_archivo}")

if __name__ == "__main__":
    # ¡CUIDADO! Esto generará un archivo de ~9.3 GB
    generar_gran_matriz("matriz_gigante.npy", 100000, 100000)
