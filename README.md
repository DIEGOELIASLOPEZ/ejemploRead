# 🏛 Think-Tank  

**Extraction, processing, and structured storage of medical data from a PDF file.**  

![](https://www.iimas.unam.mx/wp-content/uploads/2023/11/Logo-pagina-ok.png)

![](https://img.shields.io/github/stars/pandao/editor.md.svg) ![](https://img.shields.io/github/forks/pandao/editor.md.svg) ![](https://img.shields.io/github/tag/pandao/editor.md.svg) ![](https://img.shields.io/github/release/pandao/editor.md.svg) ![](https://img.shields.io/github/issues/pandao/editor.md.svg) ![](https://img.shields.io/bower/v/editor.md.svg)

## Tabla de Contenidos

1. [Información del Proyecto](#información-del-proyecto)
2. [Requisitos](#requisitos)
3. [📂Archivos](#archivos)
   -  header_footer_to_df.py
   - extract_tables.py
   -  utils.py
   -  main.py
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

## Archivos

### 📗 header_footer_to_df.py

Se encarga de extraer y procesar los datos generales que se encuentran en el encabezado del expediente. Estos incluyen información clave sobre el paciente, el historial clínico y detalles administrativos de la nota médica.

#### Funciones principales:
- `get_head()`
- `get_patient_data()`
- `get_medical_data()`

### 📘 extract_tables.py

Contiene un conjunto de funciones para la extracción y procesamiento de datos médicos, generando tablas específicas de secciones de un expediente médico como "Signos Vitales", "Diagnósticos Activos", y "Órdenes de Medicamentos Hospitalarios".

#### Funciones principales:
- `pdf_a_texto()`
- `extract_fecha()`
- `encontrar_seccion()`
- `eliminar_ruido()`
- `comprobacion_final()`
- `extraer_tabla()`

### 📕 utils.py

Este archivo tiene como objetivo extraer y estructurar la información médica completa de las secciones "Signos Vitales" y "Diagnósticos Activos". Los datos extraídos se organizan en un diccionario, con cada sección clave (como "Signos" y "Diagnósticos") conteniendo su respectiva información en formato de texto o DataFrame para su posterior análisis o reporte.

#### Funciones principales:
- `get_diagnosticos_activos()`
- `get_diagnosticos_para_excel()`
- `get_signos_vitales(text)`
- `get_text_from_pdf(pdf_path)`

### 📙 main.py

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

# Ejemplo de Salida.
```json
{
    "Nota_de_evolución": {
      "Header_Footer": [{
        "No_nota": "100091631",
        "Tipo_nota": "Nota de Evolución",
        "No_Expediente": "61913",
        "HIM": "872878",
        "Apellido_paterno": "Chavez",
        "Apellido_materno": "Hernandez",
        "Nombres": "Antonela Valentina",
        "Fecha_nacimiento": "29/11/2016",
        "Edad": "7 años",
        "Sexo": "Femenino",
        "Fecha_ingreso" : "13/05/2024" ,
        "Hora_ingreso" : "14:57",
        "Fecha_alta" : "",
        "Hora_alta" : "",
        "Firmado_por" : "TOVILLA GUTIÉRREZ , JOSÉ MANUEL",
        "Cedula_profesional" : "12192728",
        "Fecha_creacion" : "21/05/2024",
        "Hora_creacion" : "11:26",
        "Hospital" : "Hospital Infantil de México Federico Gómez",
        "Pronostico" : "Reservado",
        "Supervisor_nombre" :"Dr. Dávila JDCP Dr. Fernández MACCR Dr. Domínguez MACCR",
        "Nombre_Completo" : "JM Tovilla"
      }],
      "Signos_Vitales": {
        "Signos": [
          {
            "Fecha_Hora": "21/05/2024 06:29",
            "FR": "",
            "FC": "",
            "PAS": "",
            "PAD": "",
            "Sat_O2": "",
            "Temp_C": "",
            "Peso": "19.00",
            "Talla": ""
          }
        ],
        "Subjetivo": "NOTA DE EVOLUCIÓN CIRUGÍA COLORRECTAL Antonela Valentina con diagnósticos de: - Estreñimiento crónico intratable ..."
      },

      "Diagnósticos_Activos": {
        "Notas": "BH +162 ml, GU 1.35 ml/kg/h, GF Paciente femenino de edad aparente similar a cronológica, neurológicamente íntegra,normohidratada,...",
        "Examen_Físico": "",
        "Diagnósticos_Activos_tabla": [{
          "Fecha_Ingresada": "15/02/2024 10:55",
          "Descripción": "K59.0 Estreñimiento",
          "Tipo": "Diagnóstico",
          "Médico": "Castillo Santiago , Dafne",
          "Notas": ""
        }],
        "Análisis_Condición": "Valentina quien persiste con salida de material fétido a través...",
        "Comentar_estudio": ".",
        "Plan_de_Tratamiento": "Ayuno + SDB Vigilancia de condiciones abdominales Técnica de doble pañal..."
      },

      "Órdenes_de_Dietéticas_Activas": [
        {
          "Fecha_Ingresada": "15/05/2024 20:05",
          "Tipo": "NPO",
          "Tipo_terapéutico": "",
          "Notas": ""
        }
      ],

      "Órdenes_de_Enfermería_Activas": [
        {
          "Fecha_Ingresada": "17/05/2024 17:23",
          "Orden": "INSTALACIÓN DE NPT",
          "Médico": "García Solis, Dania Belem"
        }
      ],

      "Órdenes_de_Medicamentos_Hospitalarios": [
        {
          "Inicio": "21/05/2024 16:00",
          "Medicamento": "LOPERAMIDA TABLETAS 2 mg (LOPERAMIDA TABLETAS 2 mg(Gastroenterologia))",
          "Frecuencia": "Cada 8 horas",
          "Vía": "ORAL",
          "Dosis": "4.00",
          "UDM": "mg",
          "Cantidad": "2.00",
          "Tipo": "Pastilla",
          "Médico": "García Solis,Dania Belem",
          "Tasa_de_Flujo": ""
        },
        {
          "Inicio": "21/05/2024 10:34",
          "Medicamento": "OCTREOTIDA SOLUCIÓN INYECTABLE 1 mg/5 ml (OCTREOTIDA SOLUCIÓN INYECTABLE 1 mg/5 ml)",
          "Frecuencia": "Continua",
          "Vía": "INTRAVENOSA",
          "Dosis": "2000",
          "UDM": "Microgramo",
          "Cantidad": "10.00",
          "Tipo": "ml",
          "Médico": "García Solis,Dania Belem",
          "Tasa_de_Flujo": ""
        }
      ]
    }
}

```
