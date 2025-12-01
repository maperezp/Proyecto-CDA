## Proyecto de Ciencia de Datos Aplicada 2025-20

### **Integrantes:**
  - Daniel Esteban Aguilera Figueroa - d.aguilera@uniandes.edu.co
  - Diego Felipe Carvajal Lombo - df.carvajal@uniandes.edu.co
  - Jesús Manuel Ospino Bernal  - jm.ospino@uniandes.edu.co
  - María Alejandra Pérez Petro  - ma.perezp@uniandes.edu.co


### **Objetivo del Proyecto**
  - Aprovechar técnicas de Ciencia de Datos para analizar, estructurar y optimizar la información clínica de pacientes sometidos a trasplante hepático en la Fundación Santa Fe de Bogotá, con el propósito de:
  - Identificar factores de riesgo asociados a infecciones postrasplante.
  - Fortalecer la toma de decisiones clínicas y administrativas a partir de evidencia basada en datos.
  - Proponer estrategias preventivas y modelos predictivos que permitan mejorar la supervivencia y la calidad de la atención.

### **El proyecto se desarrolla en el marco del curso Ciencia de Datos Aplicada (2025-20) y contempla tres productos principales:**

1. **Power Apps – Recolección Estandarizada**
  - Aplicación digital para capturar información de pacientes trasplantados con validaciones de campos, reglas de consistencia y control de acceso por rol.
  - **Usuarios**: personal médico y administrativo.
  - **Objetivo**: mejorar la calidad y trazabilidad de los registros clínicos.
  - Link a la aplicación Power Apps:
  - https://apps.powerapps.com/play/e/default-fabd047c-ff48-492a-8bbb-8f98b9fb9cca/a/5a83b0b6-6181-41dc-a420-82b385035a78?tenantId=fabd047c-ff48-492a-8bbb-8f98b9fb9cca&hint=0dd304d1-14b7-4047-8ae7-d856a5476343&sourcetime=1764545493671&source=portal#
  
2. **Modelo de Machine Learning**
  - Algoritmo predictivo que clasifica pacientes según su riesgo de infección postrasplante hepático.
  - **Usuarios**: equipo médico e investigadores en hepatología.
  - **Objetivo**: predecir eventos infecciosos y segmentar perfiles de riesgo clínico.

3. **Dashboard en Power BI**
  - Visualización interactiva de indicadores clínicos clave (KPIs) tales como: tasa de infección, duración de cirugía, estancia en UCI, comorbilidades, estado vital y supervivencia.
  - **Usuarios**: jefes de departamento, médicos tratantes e investigadores.
  - **Objetivo**: apoyar la toma de decisiones estratégicas y el seguimiento clínico.
  - **Link**: https://app.powerbi.com/links/2LfQ-6HclV?ctid=fabd047c-ff48-492a-8bbb-8f98b9fb9cca&pbi_source=linkShare


### **Estructura del repositorio**

- docs/: Contiene toda la documentación relacionada con el desarrollo del proyecto, incluyendo reportes, esquemas, mockups y material de soporte.
- src/: Carpeta destinada al código fuente del proyecto. En este caso, incluye el notebook principal proyecto_E1_Final.ipynb, donde se documenta el flujo completo de análisis y modelado de datos.
- models/: Carpeta destinada a guardar los modelos desarrollados (pickle) para su ejecución.

### **Instrucciones de ejecución**

El código desarrollado para este proyecto se encuentra en la carpeta src, específicamente en el archivo src/proyecto_E1_Final.ipynb.
Este notebook contiene todo el proceso de análisis y tratamiento de datos.
Se deben contar con las siguientes librerías

```bash
pip install pandas numpy matplotlib seaborn
```
Los datos usados durante todo el desarrollo del proyecto (información clínica de los pacientes sometidos a trasplante hepático en la Fundación Santa Fe de Bogotá) fueron prestados a los miembros del equipo bajo un contrato de confidencialidad. Debido a esto, no es posible compartir los archivos mencionados en los documentos de desarrollo.
Link al repositorio privado de los datos:
https://github.com/Daniagui12/Proyecto-CDA-Private

El orden de ejecución de los notebookes es el siguiente:
1. 01_EDA
2. 02_generación_diccionario_de_datos
3. 03_nuevo_modelado_de_datos
4. 04_Clustering
5. 05_ClasificaciónInfecciónPostTx

En caso de requerir acceso a los datos originales o ejecutar alguno de los notebooks desarrollados durante el proyecto, será necesario contactar directamente al equipo responsable del proyecto para solicitar la autorización correspondiente y coordinar el acceso bajo las políticas de confidencialidad establecidas por la institución.



### **Conclusiones finales**
Del trabajo realizado podemos concluir que se entregaron tres productos de datos que ayudarán a la Fundación Santa Fe a mejorar el ciclo de vida de la información de los pacientes que requieren trasplante.
En primer lugar, el paso de un archivo de Excel sin controles a un esquema de gestión estructurado permitió reducir de forma notable errores de registro, valores nulos, duplicados e inconsistencias. Esto hizo que la base de datos fuera más confiable para el análisis y el modelamiento. Además, las reglas incorporadas en la aplicación para ingresar, actualizar y borrar registros evitan que reaparezcan los problemas de calidad asociados a la edición manual del Excel.
En segundo lugar, gracias a la implementación del dashboard, la Fundación cuenta ahora con una herramienta que permite analizar y tomar decisiones que pueden impactar directamente la vida de los pacientes: identificar características de los casos de fatalidad, conocer la cantidad de días promedio en UCI y explorar otras variables que contribuyen a mejorar la calidad del servicio.
De esta forma, se considera que los objetivos del proyecto se cumplieron, ya que estas herramientas fortalecen el ciclo de vida de los datos y aumentan su valor, dejando atrás la visión de un simple registro en Excel.
La principal dificultad encontrada fue la calidad de los datos y la ausencia de un diccionario de datos claro. Como se ha mencionado, la información se registraba manualmente en Excel por cada cirujano, quien definía sus propias columnas, lo que hacía extremadamente complejo cualquier esfuerzo de limpieza, análisis o construcción de modelos de machine learning.
Para mejorar las condiciones y obtener mejores resultados, es fundamental que la Fundación adopte de manera consistente la aplicación desarrollada, de modo que pueda construir una base de datos más estandarizada y limpia. Sin embargo, consideramos también que puede existir un sesgo importante debido a la limitada accesibilidad de la Fundación para pacientes de bajos recursos, lo que podría afectar los resultados. 
Por último, es necesario aclarar que los modelos obtenidos se vieron fuertemente condicionados por la calidad de los datos. Una vez se utilice la aplicación y se consolide una base más estandarizada, será posible retomar el proyecto y reentrenar o construir nuevos modelos de machine learning para mejorar sus métricas. 
