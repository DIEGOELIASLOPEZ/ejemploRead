# 🏛 Think-Tank  

**Extraction, processing, and structured storage of medical data from a PDF file.**  

![](https://www.iimas.unam.mx/wp-content/uploads/2023/11/Logo-pagina-ok.png)

![](https://img.shields.io/github/stars/pandao/editor.md.svg) ![](https://img.shields.io/github/forks/pandao/editor.md.svg) ![](https://img.shields.io/github/tag/pandao/editor.md.svg) ![](https://img.shields.io/github/release/pandao/editor.md.svg) ![](https://img.shields.io/github/issues/pandao/editor.md.svg) ![](https://img.shields.io/bower/v/editor.md.svg)


*---

## Table of Contents.
- [Project Information](#-project-information).  
- [Requirements](#-requirements).  
- [Data](#-data).  
- [File](#-file).

---

## Project Information.  
This project extracts medical information from PDF files, processes the data, and stores it in a structured format.  

### Example Output.  
 `Ejemplo_Estructura_Diccionario.json`  

---

## Requirements.
pandas==2.2.3
pdfplumber==0.11.5
PyPDF2==3.0.1


## File.

- [📄 header_footer_to_df.py](#-header-footer-to-df-py)
-  [📄extract_tables.py](#-extract_tables.py)  
-  [📄 utils.py](#- utils.py).
-  [📄main.py ](#-main)  


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
El archivo contiene un conjunto de funciones para la extracción y procesamiento de datos médicos generando tablas específicas de secciones de un expediente médico, como "Signos Vitales", "Diagnósticos Activos", y "Órdenes de Medicamentos Hospitalarios".
#### Funciones principales:
- `get_diagnosticos_activos( ):`
- `get_diagnosticos_para_excel( ):`
- `get_signos_vitales(text):`
- `get_text_from_pdf(pdf_path):`






