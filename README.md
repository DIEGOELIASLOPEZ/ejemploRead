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
