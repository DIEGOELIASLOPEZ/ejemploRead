# 🏛 Think-Tank  

**Extraction, processing, and structured storage of medical data from a PDF file.**  

![](https://www.iimas.unam.mx/wp-content/uploads/2023/11/Logo-pagina-ok.png)

![](https://img.shields.io/github/stars/pandao/editor.md.svg) ![](https://img.shields.io/github/forks/pandao/editor.md.svg) ![](https://img.shields.io/github/tag/pandao/editor.md.svg) ![](https://img.shields.io/github/release/pandao/editor.md.svg) ![](https://img.shields.io/github/issues/pandao/editor.md.svg) ![](https://img.shields.io/bower/v/editor.md.svg)

---

## Project Information.  
This project extracts medical information from PDF files, processes the data, and stores it in a structured format.  

### Example Output.  
 `Ejemplo_Estructura_Diccionario.json`  

---

## Requirements.
- pandas==2.2.3
- pdfplumber==0.11.5
- PyPDF2==3.0.1

## Files.

- [📄 header_footer_to_df.py](#header_footer_to_df)
- [📄 extract_tables.py](#extract_tables)
- [📄 utils.py](#utils)
- [📄 main.py](#main)

### header_footer_to_df.py
Se encarga de extraer y procesar los datos generales que se encuentran en el encabezado del expediente. Estos datos incluyen información clave sobre el paciente, el historial clínico y los detalles administrativos de la nota médica. 

#### Funciones principales:  
- `get_head( )`
- `get_patient_data() :`
- `get_mediacal_data( ):`

### extract_tables.py
El archivo contiene un conjunto de funciones para la extracción y procesamiento de datos médicos generando tablas específicas de secciones de un expediente médico, como "Signos Vitales", "Diagnósticos Activos", y "Órdenes de Medicamentos Hospitalarios".
#### Funciones principales:
- `pdf_a_texto( ):`
- `extract_fecha( ):`
- `econtrar_seccion( )`
- `eliminar_ruido( )`
- `comprobacion_final( )`
- `extraer_tabla( ):`

### utils.py
Este archivo `utils.py` tiene como objetivo extraer y estructurar en su totalidad la información médica de las secciones "Signos Vitales" y "Diagnósticos Activos". Los datos extraídos se organizan en un diccionario, con cada sección clave (como "Signos" y "Diagnósticos") conteniendo su respectiva información en formato de texto o DataFrame para su posterior análisis o reporte.
#### Funciones principales:
- `get_diagnosticos_activos( ):`
- `get_diagnosticos_para_excel( ):`
- `get_signos_vitales(text):`
- `get_text_from_pdf(pdf_path):`

## main.py
Archivo principal del proyecto, se encarga de coordinar la extracción, procesamiento y almacenamiento de los datos en un `diccionario.json`.

## Funcionalidad

1. Carga el archivo PDF desde la ruta especificada.
2. Extrae los datos del encabezado y pie de página utilizando las funciones del archivo [`header_footer_to_df.py`](#header_footer_to_df).
3. Extrae los datos de cada sección usando las funciones de [`extract_tables.py`](#extract_tables) y [`utils.py`](#utils).
4. Organiza la información en un diccionario estructurado.
5. Guarda los datos en una variable en formato JSON.

### Configuración de la ruta del PDF

Antes de ejecutar el script, es necesario definir la ruta del archivo PDF en la variable global `ruta_pdf`. Una vez que la ruta esté configurada correctamente, el programa estará listo para ejecutarse.

Ejemplo de cómo especificar la ruta dentro del script:

```python
ruta_pdf = "C:/Users/Usuario/Escritorio/think-tank/data/archivo.pdf"  # Windows
ruta_pdf = "/home/usuario/Escritorio/think-tank/data/archivo.pdf"  # Linux
