# ✈️ Agente de Planificación de Viaje

Este proyecto implementa un **agente automático de planificación de viajes** basado en cadenas secuenciales de LLM (`LLMChain`).  
El sistema construye un plan de viaje completo a partir de una solicitud simple de usuario, generando vuelos, alojamiento, itinerario turístico y documentos de visado de manera automática.

---

## 📌 Estructura General

El orquestador `SequentialChain` ejecuta los siguientes módulos en orden:

| Módulo                  | Descripción                                                                                  |
|--------------------------|----------------------------------------------------------------------------------------------|
| `flight_chain`           | Sugiere vuelos de ida y regreso, incluyendo aerolíneas y fechas tentativas.                   |
| `lodging_chain`          | Recomienda alojamientos basados en el destino, fechas y presupuesto (si se proporciona).      |
| `tour_chain`             | Crea un itinerario turístico diario, con actividades culturales, recreativas y gastronómicas. |
| `embassy_chain`          | Enumera los requisitos de visado necesarios según el destino y la duración del viaje.          |
| `document_chain`         | Redacta las cartas y documentos solicitados por la embajada.                                   |
| `validation_chain`       | Revisa y corrige incoherencias en los documentos generados.                                    |
| `presenta_chain`         | Compila y presenta todo el plan de viaje final de forma detallada y amigable.                  |

---

## 🧠 Lógica de Funcionamiento

- El usuario proporciona una **solicitud libre** describiendo su deseo de viaje (ej. "quiero viajar a París en junio").
- El agente analiza y completa la planificación **sin hacer preguntas adicionales**.
- Si faltan detalles (como presupuesto o fechas exactas), el agente:
  - Sugiere **múltiples opciones** (económica, media, premium).
  - Hace **asunciones razonables** basadas en prácticas comunes.

---

## 🎯 Características Destacadas

- **Respuesta multi-opción** para presupuestos no especificados.
- **Formalidad y detalle** en documentos de soporte para visas.
- **Formato estructurado** en todas las respuestas (listas, tablas, secciones claras).
- **Validación automática** de documentos generados.
- **Presentación final profesional** lista para usar en solicitudes oficiales o embajadas.

---

## 🚀 Ejemplo de Flujo

1. **Entrada del usuario:**  
   `"Quiero viajar a Roma en septiembre, no tengo fechas fijas ni presupuesto definido."`

2. **Salida del agente:**  
   - Sugerencia de 3 alternativas de vuelo y hotel.
   - Itinerario detallado día por día.
   - Requisitos de visa para Italia.
   - Cartas de soporte redactadas y validadas.
   - Todo presentado en un documento final amigable y organizado.

---

## ⚙️ Tecnologías Utilizadas

- **LangChain**: construcción de `LLMChain` y `SequentialChain`.
- **Modelo LLM**: configurable (`OpenAI`, `Anthropic`, etc.).
- **Python 3.11+**

---

## 📋 Recomendaciones Futuras
- Modularizar los prompts para fácil actualización.
- Agregar soporte a múltiples destinos en el mismo viaje.
- Integrar validaciones contra APIs reales de vuelos y hoteles (opcional).
- Agregar una interfaz gráfica web con Streamlit.

