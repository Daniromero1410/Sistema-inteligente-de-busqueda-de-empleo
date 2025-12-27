# Sistema de Búsqueda Inteligente de Empleo

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![BeautifulSoup](https://img.shields.io/badge/BeautifulSoup-4.0+-green.svg)](https://www.crummy.com/software/BeautifulSoup/)
[![PyPDF2](https://img.shields.io/badge/PyPDF2-3.0+-red.svg)](https://pypdf2.readthedocs.io/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Sistema automatizado de búsqueda de empleo que analiza hojas de vida en PDF y encuentra ofertas laborales personalizadas en portales de empleo colombianos.

## Descripción del Proyecto

Sistema inteligente que combina análisis de CV con web scraping para automatizar la búsqueda de empleo. Diseñado específicamente para profesionales colombianos buscando oportunidades en Bucaramanga y trabajo remoto.

### Características Principales

**Análisis Automático de CV**
- Extracción de información de hojas de vida en PDF
- Reconocimiento de datos de contacto (email, teléfono, ubicación)
- Identificación de educación y títulos
- Detección de habilidades técnicas y blandas
- Cálculo automático de años de experiencia
- Identificación de roles objetivo

**Búsqueda Multi-Estrategia**
- Web scraping de portales de empleo colombianos
- Búsqueda en Computrabajo, ElEmpleo, Indeed
- Generación de ofertas basadas en perfil
- Búsqueda por palabras clave
- Eliminación de duplicados

**Ranking Inteligente**
- Coincidencia de habilidades
- Relevancia por ubicación
- Score de compatibilidad
- Recomendaciones personalizadas

**Exportación de Resultados**
- Resumen ejecutivo de perfil
- Lista de ofertas rankeadas
- Información de contacto de reclutadores
- Enlaces directos a postulaciones

## Funcionalidades

### 1. Análisis de Hoja de Vida

El sistema extrae automáticamente:

**Información Personal:**
- Nombre completo
- Email de contacto
- Teléfono
- Ubicación (ciudad)

**Educación:**
- Títulos universitarios
- Títulos técnicos/tecnológicos
- Áreas de estudio

**Experiencia:**
- Cálculo de años de experiencia
- Identificación de roles previos
- Extracción de fechas de trabajo

**Habilidades:**
- Técnicas: Python, Java, diseño gráfico, edición de video, etc.
- Blandas: liderazgo, trabajo en equipo, creatividad, etc.

**Roles Objetivo:**
- Identificación automática basada en experiencia
- Sugerencias de posiciones compatibles

### 2. Búsqueda de Ofertas

**Estrategia 1: Web Scraping Directo**
- Computrabajo Colombia
- ElEmpleo.com
- Indeed Colombia

**Estrategia 2: Generación Basada en Perfil**
- Ofertas simuladas realistas
- Basadas en habilidades y experiencia
- Ubicación personalizada

**Estrategia 3: Búsqueda por Palabras Clave**
- Términos extraídos del CV
- Combinaciones inteligentes
- Filtrado por relevancia

### 3. Ranking y Recomendaciones

**Sistema de Puntuación:**
- Coincidencia de habilidades (40%)
- Ubicación preferida (30%)
- Años de experiencia (20%)
- Palabras clave en título (10%)

**Filtrado:**
- Eliminación de duplicados
- Verificación de relevancia
- Ordenamiento por compatibilidad

## Estructura del Proyecto

```
job-search-automation/
├── README.md                          # Este archivo
├── LICENSE                            # Licencia MIT
├── .gitignore                         # Exclusiones de Git
├── requirements.txt                   # Dependencias Python
└── Busqueda_Empleo_Inteligente.ipynb # Notebook principal
```

## Stack Tecnológico

### Librerías Core

```
Python 3.8+
├── Análisis de PDF
│   └── PyPDF2
├── Web Scraping
│   ├── requests
│   ├── BeautifulSoup4
│   └── lxml
├── Procesamiento de Datos
│   ├── re (expresiones regulares)
│   └── json
└── Utilidades
    ├── datetime
    └── typing
```

### Capacidades

- **PyPDF2**: Extracción de texto de archivos PDF
- **BeautifulSoup**: Parsing de HTML
- **requests**: Peticiones HTTP
- **re**: Análisis de patrones en texto
- **typing**: Type hints para mejor código

## Instalación y Uso

### Opción 1: Google Colab (Recomendado)

El notebook está optimizado para Google Colab:

1. Abrir `Busqueda_Empleo_Inteligente.ipynb` en Google Colab
2. Ejecutar la primera celda para instalar dependencias
3. Subir tu hoja de vida en PDF cuando se solicite
4. Seguir las instrucciones interactivas
5. Recibir recomendaciones personalizadas

### Opción 2: Instalación Local

```bash
# Clonar repositorio
git clone https://github.com/Daniromero1410/job-search-automation.git
cd job-search-automation

# Crear entorno virtual
python -m venv venv
source venv/bin/activate  # Linux/Mac
# o
venv\Scripts\activate  # Windows

# Instalar dependencias
pip install -r requirements.txt

# Ejecutar Jupyter Notebook
jupyter notebook Busqueda_Empleo_Inteligente.ipynb
```

## Guía de Uso Paso a Paso

### Paso 1: Preparar Hoja de Vida

Asegurarse que tu CV en PDF contenga:
- Nombre completo
- Información de contacto
- Educación
- Experiencia laboral con fechas
- Habilidades técnicas
- Ubicación

### Paso 2: Ejecutar el Sistema

```python
# 1. Instalar dependencias (primera celda)
!pip install PyPDF2 requests beautifulsoup4 lxml

# 2. Importar clases
from google.colab import files
analyzer = CVAnalyzer()
search_engine = JobSearchEngine()

# 3. Subir CV
uploaded = files.upload()
pdf_file = list(uploaded.keys())[0]

# 4. Analizar CV
profile = analyzer.analyze_cv(pdf_file)

# 5. Buscar ofertas
jobs = search_engine.search_jobs(profile, "Bucaramanga")

# 6. Ver resultados
search_engine.display_results(jobs)
```

### Paso 3: Revisar Resultados

El sistema muestra:
- Resumen de tu perfil profesional
- Lista de ofertas rankeadas
- Información de cada oferta (empresa, ubicación, salario)
- Enlaces directos para postular
- Score de compatibilidad

## Ejemplo de Salida

```
════════════════════════════════════════════════════════════════════
📋 RESUMEN DE TU PERFIL
════════════════════════════════════════════════════════════════════

👤 Nombre: Juan Pérez
📍 Ubicación: Bucaramanga, Santander
📧 Email: juan.perez@email.com
📱 Teléfono: 300-123-4567
💼 Experiencia: 3.5 años

🎓 EDUCACIÓN:
• Universitaria - Ingeniería de Sistemas

🔧 HABILIDADES TÉCNICAS:
Python, JavaScript, SQL, React, Node.js

💡 HABILIDADES BLANDAS:
liderazgo, trabajo en equipo, resolución de problemas

🎯 ROLES OBJETIVO:
• Desarrollador Web
• Ingeniero de Software
• Analista de Datos

════════════════════════════════════════════════════════════════════
🎯 OFERTAS RECOMENDADAS (Top 10)
════════════════════════════════════════════════════════════════════

[1] ⭐ Desarrollador Full Stack
    🏢 TechCorp Colombia
    📍 Bucaramanga (Híbrido)
    💰 $3,500,000 - $4,500,000
    🔗 https://www.computrabajo.com/...
    ✨ Score: 95% - Excelente match

[2] ⭐ Ingeniero de Software Jr
    🏢 Software Solutions
    📍 Remoto
    💰 $3,000,000 - $4,000,000
    🔗 https://www.elempleo.com/...
    ✨ Score: 88% - Muy buen match

...
```

## Portales de Empleo Soportados

### Portales Colombianos

**Computrabajo**
- URL: https://www.computrabajo.com.co
- Cobertura: Nacional
- Categorías: Todas las industrias

**ElEmpleo**
- URL: https://www.elempleo.com
- Cobertura: Nacional
- Categorías: Profesionales y técnicos

**Indeed**
- URL: https://co.indeed.com
- Cobertura: Nacional e internacional
- Categorías: Todas las industrias

### Regiones Soportadas

- Bucaramanga (principal)
- Bogotá
- Medellín
- Cali
- Trabajo Remoto

## Habilidades Reconocidas

### Técnicas

**Programación:**
Python, Java, JavaScript, C++, SQL, HTML, CSS, React, Node.js

**Diseño:**
Photoshop, Illustrator, InDesign, Figma, Sketch, Canva

**Video y Multimedia:**
Premiere, After Effects, Lightroom, edición de video

**Análisis de Datos:**
Excel, Power BI, Tableau, Google Analytics

**Marketing Digital:**
SEO, SEM, redes sociales, marketing digital

### Blandas

Liderazgo, trabajo en equipo, creatividad, responsabilidad, adaptabilidad, comunicación, resolución de problemas, pensamiento crítico, organización, gestión del tiempo

## Algoritmo de Ranking

### Cálculo de Score

```python
score = (
    habilidades_match * 0.40 +
    ubicacion_match * 0.30 +
    experiencia_match * 0.20 +
    titulo_match * 0.10
)
```

**Habilidades Match (40%):**
- Porcentaje de habilidades del candidato que coinciden con la oferta

**Ubicación Match (30%):**
- 100% si coincide ciudad preferida
- 80% si es remoto
- 50% si es otra ciudad

**Experiencia Match (20%):**
- Basado en años de experiencia vs. requerimientos

**Título Match (10%):**
- Coincidencia de palabras clave en título del puesto

## Características Avanzadas

### Análisis de Experiencia

El sistema calcula automáticamente años de experiencia:

```python
# Reconoce formatos:
"Enero 2020 - Actualidad"
"2019 - 2023"
"01/2020 - 12/2023"
"3 años de experiencia"
```

### Extracción de Contacto

Detecta automáticamente:

```python
# Email
email_pattern = r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b'

# Teléfono
phone_pattern = r'\b\d{3}[-.]?\d{3}[-.]?\d{4}\b'

# Ubicación
ciudades = ['Bucaramanga', 'Bogotá', 'Medellín', 'Cali', ...]
```

### Identificación de Roles

Mapeo inteligente de habilidades a roles:

```python
role_keywords = {
    'Desarrollador Web': ['html', 'css', 'javascript', 'web'],
    'Diseñador Gráfico': ['diseño gráfico', 'illustrator', 'indesign'],
    'Community Manager': ['redes sociales', 'marketing digital'],
    ...
}
```

## Casos de Uso

### Profesionales Recién Graduados
- Primera búsqueda de empleo
- Identificación de posiciones junior
- Construcción de perfil profesional

### Profesionales en Transición
- Cambio de industria
- Búsqueda de nuevas oportunidades
- Actualización de perfil

### Freelancers
- Búsqueda de proyectos
- Oportunidades remotas
- Diversificación de clientes

### Cazatalentos y Reclutadores
- Búsqueda inversa de candidatos
- Análisis de mercado laboral
- Benchmarking salarial

## Limitaciones y Consideraciones

### Limitaciones Técnicas

**Web Scraping:**
- Dependiente de estructura de sitios web
- Puede requerir actualización si cambian diseños
- Rate limiting de algunos portales

**Análisis de PDF:**
- Funciona mejor con PDFs de texto (no escaneados)
- Formato de CV afecta extracción
- Requiere estructura relativamente estándar

**Cobertura:**
- Enfocado en Colombia
- Portales principales únicamente
- No incluye LinkedIn (requiere API)

### Consideraciones Legales

**Uso Responsable:**
- Respetar términos de servicio de portales
- No hacer scraping abusivo (rate limiting)
- Uso personal y educativo

**Privacidad:**
- CVs procesados localmente
- No se almacena información personal
- Usuario controla sus datos

## Mejoras Futuras

### Corto Plazo
- Integración con LinkedIn API
- Soporte para más portales
- Mejora de algoritmo de ranking
- Dashboard interactivo

### Mediano Plazo
- Aplicación automática a ofertas
- Seguimiento de postulaciones
- Alertas de nuevas ofertas
- Análisis de tendencias salariales

### Largo Plazo
- Machine learning para mejor matching
- Sistema de recomendaciones
- Análisis predictivo de mercado
- Integración con ATS

## Troubleshooting

### Problemas Comunes

**PDF no se extrae correctamente:**
```python
# Solución: Verificar que sea PDF de texto, no escaneado
# Convertir PDF escaneado con OCR primero
```

**No encuentra ofertas:**
```python
# Solución: 
# 1. Verificar conexión a internet
# 2. Revisar que habilidades estén bien escritas
# 3. Ampliar búsqueda a más ciudades
```

**Errores de scraping:**
```python
# Solución:
# 1. Verificar que portales estén accesibles
# 2. Ajustar delays entre requests
# 3. Actualizar selectores si cambiaron sitios
```

## Contribuciones

Este proyecto está abierto a contribuciones. Áreas de interés:

- Soporte para nuevos portales de empleo
- Mejoras en algoritmo de extracción de PDF
- Optimización de algoritmo de ranking
- Nuevas funcionalidades

## Autor

**Daniel Romero**  
Ingeniero Civil - Especialista en Automatización y Análisis de Datos

**Afiliación:**  
Universidad de Santander (UDES)  
Bucaramanga, Santander, Colombia

**Contacto:**  
- Email: danielromero.software@gmail.com
- LinkedIn: [daniromerosoftware](https://www.linkedin.com/in/daniromerosoftware)
- GitHub: [Daniromero1410](https://github.com/Daniromero1410)

## Licencia

MIT License - Ver archivo LICENSE para detalles

Este software se proporciona con fines educativos y de investigación. El uso de web scraping debe cumplir con los términos de servicio de los sitios web objetivo.

## Disclaimer

Este proyecto es una herramienta de asistencia para búsqueda de empleo. No garantiza la obtención de trabajo ni reemplaza el networking profesional y la preparación para entrevistas.

Los resultados dependen de:
- Calidad de la hoja de vida
- Estado del mercado laboral
- Disponibilidad de ofertas
- Coincidencia de perfil

## Agradecimientos

- Portales de empleo colombianos por facilitar información pública
- Comunidad open-source por las librerías utilizadas
- Profesionales que contribuyeron con feedback

---

**Versión:** 1.0  
**Última actualización:** Diciembre 2024  
**Estado:** Proyecto activo  
**Tipo:** Herramienta de automatización laboral
