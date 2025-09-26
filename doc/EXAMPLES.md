# 📚 Ejemplos de Uso y Casos de Prueba

## 🎯 Casos de Uso Reales

### Caso 1: Desarrollador Frontend Buscando Trabajo

**Perfil del Usuario:**
- Profesión: Desarrollador Frontend
- Experiencia: 3 años
- Ubicación: Madrid, España
- CV: PDF con experiencia en React, JavaScript, CSS

**Flujo Esperado:**
1. Usuario sube CV de desarrollador frontend
2. Sistema extrae: React, JavaScript, CSS, HTML, Git
3. Genera perfiles: "Frontend Developer Madrid", "React Developer España"
4. Busca ofertas relacionadas con frontend en Madrid
5. Calcula compatibilidad basada en tecnologías coincidentes
6. Envía email con ofertas de React, JavaScript, etc.

**Resultado Esperado:**
- 5-10 ofertas de frontend en Madrid
- Scores de compatibilidad 70-95%
- Enlaces directos para postularse

### Caso 2: Marketing Digital con Experiencia Internacional

**Perfil del Usuario:**
- Profesión: Marketing Digital
- Experiencia: 5 años
- Ubicación: Barcelona, España
- CV: Imagen con experiencia en Google Ads, SEO, Analytics

**Flujo Esperado:**
1. Usuario sube CV de marketing digital
2. Sistema extrae: Google Ads, SEO, Analytics, Social Media
3. Genera perfiles: "Digital Marketing Barcelona", "SEO Specialist España"
4. Busca ofertas de marketing digital en Barcelona
5. Calcula compatibilidad basada en herramientas y experiencia
6. Envía email con ofertas de marketing digital

**Resultado Esperado:**
- 8-12 ofertas de marketing digital
- Scores de compatibilidad 60-90%
- Ofertas de diferentes niveles (junior, senior, manager)

### Caso 3: Recién Graduado en Administración

**Perfil del Usuario:**
- Profesión: Administración de Empresas
- Experiencia: 0 años (recién graduado)
- Ubicación: Valencia, España
- CV: PDF con estudios universitarios y prácticas

**Flujo Esperado:**
1. Usuario sube CV de recién graduado
2. Sistema extrae: Estudios universitarios, prácticas, habilidades básicas
3. Genera perfiles: "Administrativo Valencia", "Junior Business Analyst España"
4. Busca ofertas para recién graduados en Valencia
5. Calcula compatibilidad basada en estudios y habilidades transferibles
6. Envía email con ofertas de nivel junior

**Resultado Esperado:**
- 3-7 ofertas para recién graduados
- Scores de compatibilidad 40-70%
- Ofertas de formación y desarrollo profesional

## 🧪 Casos de Prueba Técnicos

### Prueba 1: Validación de Formatos de Archivo

**Objetivo:** Verificar que el sistema procese correctamente diferentes formatos

**Archivos de Prueba:**
```bash
# Archivos válidos
- CV_Desarrollador.pdf (2MB)
- CV_Marketing.png (1.5MB)
- CV_Admin.jpg (800KB)

# Archivos inválidos (deben fallar)
- CV_Word.doc (no soportado)
- CV_Corrupto.pdf (archivo dañado)
- Archivo_Vacio.pdf (0 bytes)
```

**Resultados Esperados:**
- ✅ PDF, PNG, JPG: Procesamiento exitoso
- ❌ DOC, archivos corruptos: Error manejado correctamente

### Prueba 2: Límites de Tamaño de Archivo

**Objetivo:** Verificar manejo de archivos grandes

**Archivos de Prueba:**
```bash
# Diferentes tamaños
- CV_Pequeño.pdf (100KB)
- CV_Mediano.pdf (2MB)
- CV_Grande.pdf (10MB)
- CV_Muy_Grande.pdf (50MB)
```

**Resultados Esperados:**
- ✅ Hasta 10MB: Procesamiento normal
- ⚠️ 10-20MB: Procesamiento lento pero exitoso
- ❌ >20MB: Error de límite de tamaño

### Prueba 3: Idiomas Diferentes

**Objetivo:** Verificar procesamiento de CVs en diferentes idiomas

**Archivos de Prueba:**
```bash
# CVs en diferentes idiomas
- CV_Espanol.pdf (español)
- CV_English.pdf (inglés)
- CV_Francais.pdf (francés)
- CV_Deutsch.pdf (alemán)
```

**Resultados Esperados:**
- ✅ Español: Análisis completo en español
- ✅ Inglés: Análisis completo en inglés
- ⚠️ Otros idiomas: Análisis básico o traducción automática

## 📊 Ejemplos de Datos de Entrada y Salida

### Entrada del Formulario

```json
{
  "Email": "candidato@ejemplo.com",
  "CV": {
    "filename": "CV_Desarrollador_Frontend.pdf",
    "mimetype": "application/pdf",
    "size": 2048576,
    "data": "base64_encoded_data..."
  }
}
```

### Salida del AI Agent

```json
{
  "profiles": [
    {
      "Query": "Desarrollador Frontend",
      "Country": "ES",
      "Language": "es",
      "Job_requirements": "more_than_3_years_experience",
      "Location": "Madrid"
    },
    {
      "Query": "React Developer",
      "Country": "ES", 
      "Language": "es",
      "Job_requirements": "more_than_3_years_experience",
      "Location": "Barcelona"
    }
  ],
  "cv_feedback": {
    "strengths": [
      "Experiencia sólida en React y JavaScript",
      "Conocimientos avanzados en CSS y HTML5",
      "Experiencia con Git y metodologías ágiles"
    ],
    "improvements": [
      "Considera aprender TypeScript",
      "Añade experiencia con testing automatizado",
      "Incluye proyectos personales en GitHub"
    ],
    "suggested_rewrite": "Desarrollador Frontend con 3 años de experiencia en React, JavaScript y CSS. Especializado en desarrollo de interfaces de usuario responsivas y aplicaciones web modernas.",
    "skills": [
      "React",
      "JavaScript", 
      "CSS",
      "HTML5",
      "Git",
      "Node.js",
      "Webpack"
    ]
  }
}
```

### Resultado de Búsqueda de Ofertas

```json
{
  "data": [
    {
      "job_id": "12345",
      "employer_name": "TechCorp Madrid",
      "job_title": "Desarrollador Frontend React",
      "job_location": "Madrid, España",
      "job_employment_type": "Tiempo completo",
      "job_description": "Buscamos desarrollador frontend con experiencia en React...",
      "apply_options": [
        {
          "publisher": "LinkedIn",
          "apply_link": "https://linkedin.com/jobs/12345"
        }
      ]
    }
  ]
}
```

### Resultado del Scoring

```json
{
  "job_id": "12345",
  "match_score": 87,
  "matched_skills": [
    "React",
    "JavaScript",
    "CSS",
    "HTML5"
  ],
  "note": "Excelente coincidencia. El candidato tiene experiencia sólida en todas las tecnologías principales requeridas. Solo falta experiencia con TypeScript."
}
```

### Email Final Generado

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Resultados de Búsqueda de Empleo</title>
</head>
<body>
  <table width="100%" cellpadding="0" cellspacing="0" style="font-family:Arial,sans-serif;color:#333;background:#fff;">
    <tr>
      <td style="padding:20px;">
        
        <!-- Saludo -->
        <h2>Hola candidato,</h2>
        <p>Aquí tienes el análisis de tu CV y los resultados de búsqueda de vacantes en tu ciudad.</p>
        
        <!-- Análisis de CV -->
        <h3>Análisis de tu CV</h3>
        <h4>Resumen sugerido</h4>
        <p>Desarrollador Frontend con 3 años de experiencia en React, JavaScript y CSS...</p>
        
        <h4>Fortalezas</h4>
        <ul>
          <li>Experiencia sólida en React y JavaScript</li>
          <li>Conocimientos avanzados en CSS y HTML5</li>
          <li>Experiencia con Git y metodologías ágiles</li>
        </ul>
        
        <h4>Áreas de mejora</h4>
        <ul>
          <li>Considera aprender TypeScript</li>
          <li>Añade experiencia con testing automatizado</li>
          <li>Incluye proyectos personales en GitHub</li>
        </ul>
        
        <!-- Ofertas encontradas -->
        <h3>Ofertas Encontradas</h3>
        
        <div style="border:1px solid #ddd; border-radius:8px; background:#f5f5f5; margin-bottom:20px; padding:15px;">
          <h4>TechCorp Madrid - Desarrollador Frontend React</h4>
          <p>📍 Madrid, España | 💼 Tiempo completo</p>
          
          <div style="background-color:#fff9e5; border:1px solid #f5a623; border-radius:6px; padding:10px; margin:12px 0;">
            <p><strong>Match: 87%</strong></p>
            <p>Excelente coincidencia. El candidato tiene experiencia sólida en todas las tecnologías principales requeridas.</p>
            <p>Habilidades coincidentes:</p>
            <ul>
              <li>React</li>
              <li>JavaScript</li>
              <li>CSS</li>
              <li>HTML5</li>
            </ul>
          </div>
          
          <a href="https://linkedin.com/jobs/12345" target="_blank" style="display:inline-block; padding:6px 8px; background-color:#1a73e8; color:#fff; text-decoration:none; border-radius:4px;">
            Postularse en LinkedIn
          </a>
        </div>
        
      </td>
    </tr>
  </table>
</body>
</html>
```

## 🔧 Casos de Prueba de Configuración

### Prueba 1: Configuración de Credenciales

**Objetivo:** Verificar que todas las credenciales estén configuradas correctamente

**Pasos:**
1. Verificar que existan las 4 credenciales requeridas
2. Probar cada credencial individualmente
3. Verificar que los nombres coincidan exactamente

**Resultados Esperados:**
- ✅ Todas las credenciales configuradas
- ✅ Nombres exactos: "Mistral Cloud account", "OpenAi account", etc.
- ✅ APIs responden correctamente

### Prueba 2: Conectividad de APIs

**Objetivo:** Verificar que todas las APIs externas estén accesibles

**Pasos:**
1. Probar conexión a Mistral AI
2. Probar conexión a OpenAI
3. Probar conexión a RapidAPI
4. Probar conexión a Gmail API

**Resultados Esperados:**
- ✅ Todas las APIs responden
- ✅ Límites de rate limiting respetados
- ✅ Autenticación exitosa

### Prueba 3: Flujo Completo End-to-End

**Objetivo:** Verificar que todo el flujo funcione correctamente

**Pasos:**
1. Subir CV de prueba
2. Monitorear ejecución paso a paso
3. Verificar que se reciba el email
4. Validar contenido del email

**Resultados Esperados:**
- ✅ Ejecución sin errores
- ✅ Email recibido en 2-5 minutos
- ✅ Contenido del email correcto y completo

## 📈 Métricas de Rendimiento

### Tiempos de Ejecución Esperados

```bash
# Tiempos típicos por etapa
Extracción de texto:     10-30 segundos
Análisis de CV:          15-45 segundos  
Búsqueda de ofertas:     5-15 segundos
Cálculo de scoring:      10-30 segundos
Formato y envío:        5-10 segundos
----------------------------------------
Total:                  45-130 segundos
```

### Límites de Uso

```bash
# Límites por servicio
Mistral AI:              100 requests/día (plan gratuito)
OpenAI:                  3 requests/minuto (plan gratuito)
RapidAPI JSearch:        100 requests/mes (plan gratuito)
Gmail:                   Sin límites significativos
```

## 🚨 Casos de Error y Manejo

### Error: Archivo no soportado

**Entrada:**
```json
{
  "Email": "test@ejemplo.com",
  "CV": {
    "filename": "CV_Word.doc",
    "mimetype": "application/msword"
  }
}
```

**Comportamiento Esperado:**
- El Switch node no encuentra coincidencia
- El workflow se detiene sin error
- Se envía email de error al usuario

### Error: API no disponible

**Escenario:** RapidAPI temporalmente no disponible

**Comportamiento Esperado:**
- El nodo HTTP Request falla
- Se activa el workflow de error
- Se envía notificación al administrador
- Se registra el error en logs

### Error: Credenciales inválidas

**Escenario:** API key de OpenAI expirada

**Comportamiento Esperado:**
- El nodo OpenAI falla con error de autenticación
- Se registra el error en logs de n8n
- Se envía notificación al administrador
- El workflow se detiene sin procesar

---

**¡Casos de prueba completados!** 🎉

Estos ejemplos te ayudarán a validar que tu sistema funciona correctamente en diferentes escenarios.
