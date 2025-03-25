# 🏛 Think-Tank  

**Extraction, processing, and structured storage of medical data from a PDF file.**  

![](https://www.iimas.unam.mx/wp-content/uploads/2023/11/Logo-pagina-ok.png)


## Tabla de Contenidos
*Haz click en la sección que deseas consultar*

1. [**🧾Información del Proyecto**](#información-del-proyecto)
2. [📋**Requisitos**](#requisitos)
3. [📂**Archivos**](#archivos)
   -  [📗**header_footer_to_df.py**](#header_footer_to_dfpy)
   - [📘**extract_tables.py**](#extract_tablespy)
   -  [ 📙**utils.py**](#utilspy)
   -  [ 📕**main.py**](#mainpy)
4. [📄**Uso**](#uso)
5. [📜**Ejemplo de Salida**](#ejemplo-de-salida)
---

## Información del Proyecto

Este proyecto extrae información médica desde archivos PDF, procesa los datos y los almacena en un formato estructurado.

## Requisitos

- `pandas==2.2.3`
- `pdfplumber==0.11.5`
- `PyPDF2==3.0.1`

---

## Archivos

### header_footer_to_df.py

Se encarga de extraer y procesar los datos generales que se encuentran en el encabezado del expediente. Estos incluyen información clave sobre el paciente, el historial clínico y detalles administrativos de la nota médica.

#### Funciones principales:
- `get_head()`
- `get_patient_data()`
- `get_medical_data()`

### extract_tables.py

Contiene un conjunto de funciones para la extracción y procesamiento de datos médicos, generando tablas específicas de secciones de un expediente médico como "Signos Vitales", "Diagnósticos Activos", y "Órdenes de Medicamentos Hospitalarios".

#### Funciones principales:
- `pdf_a_texto()`
- `extract_fecha()`
- `encontrar_seccion()`
- `eliminar_ruido()`
- `comprobacion_final()`
- `extraer_tabla()`

### utils.py

Este archivo tiene como objetivo extraer y estructurar la información médica completa de las secciones "Signos Vitales" y "Diagnósticos Activos". Los datos extraídos se organizan en un diccionario, con cada sección clave (como "Signos" y "Diagnósticos") conteniendo su respectiva información en formato de texto o DataFrame para su posterior análisis o reporte.

#### Funciones principales:
- `get_diagnosticos_activos()`
- `get_diagnosticos_para_excel()`
- `get_signos_vitales(text)`
- `get_text_from_pdf(pdf_path)`

### main.py

#### Funciones principales:
- `df_to_dict(df, columns)`
- `get_header_footer(text)`
- `extract_and_validate(texto_extraido, seccion, columns)`
- `main()`

## Uso del main

1. Carga el archivo PDF desde la ruta especificada.
2. Extrae los datos del encabezado y pie de página utilizando las funciones de `header_footer_to_df.py`.
3. Extrae los datos de cada sección usando las funciones de `extract_tables.py` y `utils.py`.
4. Organiza la información en un diccionario estructurado.
5. Guarda los datos en formato JSON.

### Configuración de la ruta del PDF

Antes de ejecutar el script, es fundamental configurar correctamente la ruta del archivo PDF en la variable global `ruta_pdf`. Una vez que la ruta esté definida, el programa estará listo para ejecutarse.

**Ejemplo de cómo especificar la ruta dentro del script:**
Por defecto, la variable `ruta_pdf` está configurada para apuntar a la carpeta EJEMPLO NOTAS DE UN PACIENTE 7 DIAS y al archivo nota1.pdf. El valor predeterminado es el siguiente:
`ruta_pdf = "./data/EJEMPLO NOTAS DE UN PACIENTE 7 DIAS/nota1.pdf"`

Si deseas utilizar una ruta diferente, modifica la variable ruta_pdf según el sistema operativo de la siguiente manera:

    ruta_pdf = "C:/Users/Usuario/Escritorio/think-tank/data/archivo.pdf"  # Windows
    ruta_pdf = "/home/usuario/Escritorio/think-tank/data/archivo.pdf"  # Linux

# Ejemplo de Salida.

```json
{
    "note_info": {
        "No_nota": "Numero del Nota del Expediente",
        "Tipo_nota": "Tipo de Nota",
        "No_Expediente": "Numero del expediente",
        "HIM": "Identificador HIM",
        "Hospital": "Nombre del Hospital",
        "Fecha_ingreso": "Fecha en que se ingreso al hospotal en formato Datetime (AAAA-MM-DDTHH:MM:SSZ)",
        "Fecha_alta": "Fecha en que se dio de alta al hospotal en formato Datetime (AAAA-MM-DDTHH:MM:SSZ)"
    },
    "patient_info": {
        "Apellido_paterno": "Apelldio Paterno del paciente",
        "Apellido_materno": "Apelldio Materno del paciente",
        "Nombres": "Nombre(s) del paciente",
        "Fecha_nacimiento": "Fecha de nacimiento formato Datetime (AAAA-MM-DDTHH:MM:SSZ)."  ,
        "Sexo": "Sexo del paciente"
    },
    "medical_info": {
        "Nombre_Completo": "Nombre del medico que firmo",
        "Firmado_por": "Firma/Nombre del medico que firmo",
        "Supervisor_nombre": "Nombre del Supervison",
        "Cedula_profesional": "Cedula Profesional",
        "Fecha_creacion": "Fecha de creacion del expediente en formato Datetime (AAAA-MM-DDTHH:MM:SSZ)"
    },
    "sign_info": {
        "Tabla": [
            {
                "Fecha/Hora": "Fecha y Hora en formato Datetime (AAAA-MM-DDTHH:MM:SSZ)",
                "FR": "Frecuencia Respiratoria",
                "FC": "Frecuencia Cardíaca",
                "PAS": "Presión Arterial Sistólica",
                "PAD": "Presión Arterial Diastólica",
                "SAT_O2": "Saturacion",
                "Temp_°C": "Temperatura",
                "Peso": "Peso",
                "Talla": "Talla"
            }
        ],
        "Subjetivo": "Nota con descripcion del diagnostico "
    },
{
    "diagnostic_info": {
        "Examen_Físico": "Descripción del examen físico realizado al paciente, incluyendo hallazgos relevantes.",
        "Diagnósticos_Activos_Tabla": [
            {
                "Fecha_Ingresada": "Fecha y hora en que el diagnóstico fue registrado.",
                "Descripción": "Descripción detallada del diagnóstico del paciente.",
                "Tipo": "Tipo de diagnóstico, por ejemplo, diagnóstico principal o secundario.",
                "Médico": "Nombre del médico que realizó el diagnóstico."
            }
        ],
        "Análisis_Condición": "Descripción del análisis y estado clínico actual del paciente, incluyendo antecedentes relevantes, tratamiento actual y recomendaciones.",
        "Estudios": "Descripción de los estudios realizados o pendientes al paciente, incluyendo resultados previos y planes de estudios adicionales.",
        "Plan_de_Tratamiento": "Plan detallado de tratamiento propuesto para el paciente, con indicaciones específicas para su seguimiento."
    },
    "diet_info": {
        "Tabla": [
            {
                "Fecha_Ingresada": "Fecha en que se ingresó la información dietética del paciente en formato Datetime (AAAA-MM-DDTHH:MM:SSZ)",
                "Tipo": "Tipo de dieta indicada para el paciente, por ejemplo, NPO (Nada por boca), líquida, etc.",
                "Tipo_terapéutico": "Especificación del tipo de dieta terapéutica si aplica, como dieta baja en sal, controlada, etc."
            }
        ]
    },
    "nursing_info": {
        "Tabla": [
            {
                "Fecha_Ingresada": "Fecha en que se ingresó la información dietética del paciente en formato Datetime (AAAA-MM-DDTHH:MM:SSZ)",
                "Orden": " acción específica de enfermería o procedimiento realizado",
                "Médico": "Nombre del médico que realizó el diagnóstico."
            }
        ]
    },
    "medication_info": {
        "Tabla": [
            {
                "Inicio": "Fecha y hora de inicio del tratamiento con el medicamento.",
                "Medicamento": "Nombre y presentación del medicamento administrado al paciente.",
                "Frecuencia": "Frecuencia con la que se administra el medicamento, por ejemplo, cada 8 horas, continua, etc.",
                "Via": "Vía de administración del medicamento, como intravenosa, oral, etc.",
                "Dosis": "Cantidad de medicamento administrado por cada dosis.",
                "UDM": "Unidad de medida utilizada para la dosis, como miligramos, mililitros, etc.",
                "Cantidad": "Cantidad total del medicamento administrado.",
                "Tipo": "Tipo de unidad medida utilizada, como ml, mg, etc.",
                "Médico": "Nombre del médico que prescribió el medicamento."
            }
        ]
    }
}


```
