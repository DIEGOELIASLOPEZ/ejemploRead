# 🏛 Think-Tank  

**Extracción, procesamiento y almacenamiento estructurado de datos médicos desde un archivo PDF.**

![Logo](https://github.com/DIEGOELIASLOPEZ/ejemploRead/blob/main/immas.png?raw=true)

![GitHub Stars](https://img.shields.io/github/stars/pandao/editor.md.svg)
![GitHub Forks](https://img.shields.io/github/forks/pandao/editor.md.svg)
![GitHub Tags](https://img.shields.io/github/tag/pandao/editor.md.svg)
![GitHub Release](https://img.shields.io/github/release/pandao/editor.md.svg)
![GitHub Issues](https://img.shields.io/github/issues/pandao/editor.md.svg)
![Bower Version](https://img.shields.io/bower/v/editor.md.svg)

## Tabla de Contenidos

1. [Información del Proyecto](#información-del-proyecto)
2. [Requisitos](#requisitos)
3. [Archivos](#archivos)
   1. [header_footer_to_df](#header_footer_to_df)
   2. [extract_tables.py](#extract_tablespy)
   3. [utils.py](#utilspy)
   4. [main.py](#mainpy)
4. [Uso](#uso)
5. [Ejemplo de Salida](#ejemplo-de-salida)

---

## Información del Proyecto

Este proyecto extrae información médica desde archivos PDF, procesa los datos y los almacena en un formato estructurado.

## Requisitos

- `pandas==2.2.3`
- `pdfplumber==0.11.5`
- `PyPDF2==3.0.1`

---

## 📂 Archivos

### 📗 `header_footer_to_df`

Se encarga de extraer y procesar los datos generales que se encuentran en el encabezado del expediente. Estos incluyen información clave sobre el paciente, el historial clínico y detalles administrativos de la nota médica.

#### Funciones principales:
- `get_head()`
- `get_patient_data()`
- `get_medical_data()`

### 📘 `extract_tables.py`

Contiene un conjunto de funciones para la extracción y procesamiento de datos médicos, generando tablas específicas de secciones de un expediente médico como "Signos Vitales", "Diagnósticos Activos", y "Órdenes de Medicamentos Hospitalarios".

#### Funciones principales:
- `pdf_a_texto()`
- `extract_fecha()`
- `encontrar_seccion()`
- `eliminar_ruido()`
- `comprobacion_final()`
- `extraer_tabla()`

### 📕 `utils.py`

Este archivo tiene como objetivo extraer y estructurar la información médica completa de las secciones "Signos Vitales" y "Diagnósticos Activos". Los datos extraídos se organizan en un diccionario, con cada sección clave (como "Signos" y "Diagnósticos") conteniendo su respectiva información en formato de texto o DataFrame para su posterior análisis o reporte.

#### Funciones principales:
- `get_diagnosticos_activos()`
- `get_diagnosticos_para_excel()`
- `get_signos_vitales(text)`
- `get_text_from_pdf(pdf_path)`

### 📙 `main.py`

#### Funciones principales:
- `df_to_dict(df, columns)`
- `get_header_footer(text)`
- `extract_and_validate(texto_extraido, seccion, columns)`
- `main()`

## Uso

1. Carga el archivo PDF desde la ruta especificada.
2. Extrae los datos del encabezado y pie de página utilizando las funciones de `header_footer_to_df.py`.
3. Extrae los datos de cada sección usando las funciones de `extract_tables.py` y `utils.py`.
4. Organiza la información en un diccionario estructurado.
5. Guarda los datos en formato JSON.

### Configuración de la ruta del PDF

Antes de ejecutar el script, es necesario definir la ruta del archivo PDF en la variable global `ruta_pdf`. Una vez que la ruta esté configurada correctamente, el programa estará listo para ejecutarse.

Ejemplo de cómo especificar la ruta dentro del script:

    ruta_pdf = "C:/Users/Usuario/Escritorio/think-tank/data/archivo.pdf"  # Windows
    ruta_pdf = "/home/usuario/Escritorio/think-tank/data/archivo.pdf"  # Linux
