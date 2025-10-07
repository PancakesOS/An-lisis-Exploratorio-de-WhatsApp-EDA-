# Análisis Exploratorio de Datos (EDA) de Grupo de WhatsApp

Este proyecto implementa un **Análisis Exploratorio de Datos (EDA)** completo sobre el historial de un chat de **WhatsApp**, aplicando técnicas de **Ingeniería de Características** y **procesamiento de texto** para descubrir patrones de actividad, roles de comunicación y temas dominantes.

> **Nota de Privacidad:**  
> Todos los datos originales han sido anonimizados.  
> Los nombres reales fueron sustituidos por nombres de personajes de ficción (e.g., *Neo*, *Trinity*) antes de la visualización.

---

##Metodología del Proyecto

El análisis se estructura en torno al uso intensivo de **Expresiones Regulares (Regex)** para la ingesta de datos y la creación de métricas.

### 1. Ingesta y Limpieza

- **Regex:** Se utilizó una expresión regular robusta para parsear cada línea del archivo `.txt` y extraer la **fecha**, el **usuario** y el **contenido**.  
- **Normalización de Fechas:** Conversión de la cadena de tiempo (incluyendo formatos *a.m./p.m.*) a objetos `datetime` de **Pandas** para facilitar el análisis temporal.

### 2. Ingeniería de Características

- **Anonimización:** Mapeo de usuarios originales a la columna `Usuario (anonimizado)`.  
- **Clasificación con Regex:** Creación de las columnas:
  - `Tipo_Mensaje` → (Texto, Sticker, Imagen, etc.)
  - `Num_Palabras` → Conteo de palabras en cada mensaje.
  
  Todo mediante patrones de Regex para diferenciar entre contenido escrito y multimedia.

---

## Preguntas Clave Respondidas (EDA)

El proyecto incluye visualizaciones que responden a las siguientes preguntas:

| **Categoría** | **Pregunta** | **Hallazgo (Ejemplo)** |
|----------------|---------------|-------------------------|
| **Contenido** | ¿Cómo se habla en este grupo? | Nube de palabras que revela los términos más frecuentes después de un riguroso filtrado de *stopwords* y jerga. |
| **Actividad** | ¿Quiénes son los que más escriben? | Gráfica de barras que muestra el ranking de participación por usuario. |
| **Tiempo** | ¿A qué horas/días se envía más mensajes? | Distribución de mensajes por hora (identificando picos) y por día de la semana. |
| **Roles** | ¿Quién genera y quién estimula la conversación? | Gráfica apilada que compara la proporción de mensajes de texto (generadores) vs. multimedia/stickers (estimuladores) por usuario. |

---

## Otros Análisis Interesantes

Además del EDA principal, se incluyeron análisis avanzados para capturar la **dinámica social del grupo**:

### Uso de Jerga
Se utiliza una Regex para contar el uso total de palabras de jerga  
(e.g., *alv*, *pinche*, etc.) por cada usuario, identificando a los usuarios con lenguaje más coloquial.

### Tasa de Iniciación de Conversación
Se calcula el **porcentaje de mensajes** de cada usuario que **rompen largos periodos de silencio** (definidos como más de 180 minutos de inactividad).  
Esto permite diferenciar entre **iniciadores** y **respondedores** dentro del grupo.

---

## Requisitos para la Ejecución

Este proyecto fue desarrollado en una libreta de **Jupyter Notebook** y requiere las siguientes librerías:

```bash
pip install pandas numpy matplotlib seaborn wordcloud
