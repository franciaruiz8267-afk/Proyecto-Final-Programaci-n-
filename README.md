# Proyecto-Final-Programacion 
Este proyecto está diseñado para detectar señales biomédicas atreves del código presentado.    
# Proyecto de Análisis de Señales Clínicas
**Autor:** [Nicolas, Axel, Amayrani]  
**Fecha:** 16 de Mayo de 2026  
-------------------------------------------------------------------------
**Descripción:** Desarrollo y análisis de señales biomédicas a partir de datos clínicos extraídos de un archivo CSV.
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
# Si necesitas herramientas específicas de señales o estadística, descomenta las siguientes líneas:
# from scipy import signal
# import scipy.stats as stats

# Configuración estética de las gráficas
sns.set_theme(style="whitegrid")
%matplotlib inline

print("¡Bibliotecas cargadas con éxito!")
------------------------------------------------------------------
# Reemplaza 'tu_archivo.csv' por el nombre real de tu documento
ruta_archivo = 'tu_archivo.csv'

try:
    df = pd.read_csv(ruta_archivo)
    print("¡Archivo cargado correctamente!")
    print(f"El dataset tiene {df.shape[0]} filas y {df.shape[1]} columnas.")
except FileNotFoundError:
    print(f"Error: No se encontró el archivo en '{ruta_archivo}'. Verifica la ruta.")
-------------------------------------------------------------------------------------
    # 1. Vista previa de los datos
print("--- Primeros 5 registros ---")
display(df.head())

# 2. Información general (tipos de datos y valores nulos)
print("\n--- Información general del Dataset ---")
df.info()

# 3. Verificación de datos faltantes
print("\n--- Valores faltantes por columna ---")
print(df.isnull().sum())

# 4. Limpieza básica (Ejemplo: eliminar nulos si aplica, descomenta si lo necesitas)
# df = df.dropna()
---------------------------------------------------------------------------
def normalizar_senal(senal):
    """
    Función para restar la media y dividir por la desviación estándar.
    Ayuda a centrar la señal clínica.
    """
    if np.std(senal) == 0:
        return senal
    return (senal - np.mean(senal)) / np.std(senal)

# Puedes agregar aquí funciones de filtrado, detección de picos, etc.
--------------------------------------------------------------------------------
# Aquí aplicas tus funciones a las columnas del CSV o generas nuevas variables
# Ejemplo hipotético (asumiendo que tienes una columna llamada 'amplitud'):
if 'amplitud' in df.columns:
    df['senal_procesada'] = normalizar_senal(df['amplitud'])
    print("Señal procesada y guardada en la columna 'senal_procesada'.")
else:
    print("Nota: Modifica este bloque con los nombres reales de tus columnas de señal.")
    -------------------------------------------------------------------------------------
    print("--- Resumen Estadístico Descriptivo ---")
# Esto te dará la media, desviación estándar, mínimos, máximos, etc.
display(df.describe())

# Ejemplo de correlación si tienes múltiples variables numéricas
# print("\n--- Matriz de correlación ---")
# display(df.corr())
----------------------------------------------------------------------------------------
plt.figure(figsize=(12, 5))

# Ejemplo de gráfico de línea (ajusta 'tiempo' y 'senal_procesada' a tus datos)
# plt.plot(df['tiempo'], df['senal_procesada'], label='Señal Biomédica', color='crimson')

plt.title('Visualización de la Señal Clínica', fontsize=14, fontweight='bold')
plt.xlabel('Tiempo / Muestras', fontsize=12)
plt.ylabel('Amplitud Normalizada', fontsize=12)
plt.legend()
plt.tight_layout()
plt.show()
--------------------------------------------------------------------------
## Conclusiones Clínicas

A partir del análisis de los datos y el comportamiento de las señales, se observan los siguientes puntos:

* **Hallazgo 1:** [Escribe aquí qué significa fisiológicamente el comportamiento de la señal observada].
* **Hallazgo 2:** Los valores estadísticos (media, variabilidad) sugieren que...
* **Implicación Médica:** [¿Qué relevancia tiene esto para el diagnóstico o monitoreo del paciente?].
-------------------------------------------------------------------------
