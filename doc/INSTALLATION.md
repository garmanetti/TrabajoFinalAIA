# 🚀 Guía de Instalación - Sistema de Análisis de CV

## 📋 Prerrequisitos

### Requisitos del Sistema
- **n8n**: Versión 1.0 o superior
- **Navegador**: Chrome, Firefox, Safari o Edge (últimas versiones)
- **Conexión a Internet**: Para APIs externas

### Cuentas de Servicios Externos
Necesitarás cuentas activas en los siguientes servicios:

1. **Mistral AI** - [https://console.mistral.ai/](https://console.mistral.ai/)
2. **OpenAI** - [https://platform.openai.com/](https://platform.openai.com/)
3. **RapidAPI** - [https://rapidapi.com/](https://rapidapi.com/)
4. **Gmail** - Cuenta de Google con acceso a Gmail API

## 🔧 Configuración Paso a Paso

### Paso 1: Configurar Mistral AI

1. **Crear cuenta en Mistral AI**
   - Visita [https://console.mistral.ai/](https://console.mistral.ai/)
   - Regístrate o inicia sesión
   - Ve a la sección "API Keys"

2. **Generar API Key**
   ```bash
   # En la consola de Mistral AI:
   - Click en "Create API Key"
   - Nombre: "n8n-cv-analyzer"
   - Copia la clave generada
   ```

3. **Configurar en n8n**
   - Ve a Settings > Credentials
   - Click "Add Credential"
   - Selecciona "Mistral Cloud API"
   - Nombre: `Mistral Cloud account`
   - API Key: [tu clave de Mistral AI]

### Paso 2: Configurar OpenAI

1. **Crear cuenta en OpenAI**
   - Visita [https://platform.openai.com/](https://platform.openai.com/)
   - Regístrate o inicia sesión
   - Ve a "API Keys"

2. **Generar API Key**
   ```bash
   # En OpenAI Platform:
   - Click "Create new secret key"
   - Nombre: "n8n-workflow"
   - Copia la clave generada
   ```

3. **Configurar en n8n**
   - Ve a Settings > Credentials
   - Click "Add Credential"
   - Selecciona "OpenAI API"
   - Nombre: `OpenAi account`
   - API Key: [tu clave de OpenAI]

### Paso 3: Configurar RapidAPI

1. **Crear cuenta en RapidAPI**
   - Visita [https://rapidapi.com/](https://rapidapi.com/)
   - Regístrate o inicia sesión
   - Busca "JSearch" en el marketplace

2. **Suscribirse a JSearch**
   ```bash
   # En RapidAPI:
   - Busca "JSearch API"
   - Click "Subscribe to Test"
   - Selecciona el plan gratuito o de pago
   - Ve a "Endpoints" > "Search Jobs"
   ```

3. **Obtener API Key**
   ```bash
   # En la página de JSearch:
   - Ve a "Code Snippets"
   - Copia el valor de "X-RapidAPI-Key"
   ```

4. **Configurar en n8n**
   - Ve a Settings > Credentials
   - Click "Add Credential"
   - Selecciona "HTTP Header Auth"
   - Nombre: `Header RapidAPI- JSearch`
   - Header Name: `X-RapidAPI-Key`
   - Header Value: [tu clave de RapidAPI]

### Paso 4: Configurar Gmail

1. **Habilitar Gmail API**
   - Ve a [Google Cloud Console](https://console.cloud.google.com/)
   - Crea un nuevo proyecto o selecciona uno existente
   - Habilita la Gmail API

2. **Crear credenciales OAuth2**
   ```bash
   # En Google Cloud Console:
   - Ve a "Credentials"
   - Click "Create Credentials" > "OAuth 2.0 Client ID"
   - Tipo: "Web application"
   - URIs autorizados: [tu URL de n8n]
   - Descarga el archivo JSON
   ```

3. **Configurar en n8n**
   - Ve a Settings > Credentials
   - Click "Add Credential"
   - Selecciona "Gmail OAuth2"
   - Nombre: `Gmail account`
   - Client ID: [del archivo JSON]
   - Client Secret: [del archivo JSON]
   - Sigue el proceso de autorización OAuth2

## 📦 Instalación de Workflows

### Paso 1: Importar Workflows

1. **Descargar archivos**
   ```bash
   # Asegúrate de tener los siguientes archivos:
   - src/TF_Main.json
   - src/TF_SW_Extraccion_Texto.json
   ```

2. **Importar en n8n**
   ```bash
   # En n8n:
   1. Ve a "Workflows"
   2. Click "Import from file"
   3. Selecciona "TF_SW_Extraccion_Texto.json" primero
   4. Click "Import"
   5. Repite para "TF_Main.json"
   ```

### Paso 2: Verificar Configuración

1. **Verificar Subworkflow**
   - Abre "TF_SW_Extraccion_Texto"
   - Verifica que esté configurado correctamente
   - No necesita activación manual

2. **Verificar Workflow Principal**
   - Abre "TF_Main"
   - Verifica todas las conexiones
   - Verifica que las credenciales estén asignadas

### Paso 3: Activar Workflows

1. **Activar Workflow Principal**
   ```bash
   # En n8n:
   1. Abre "TF_Main"
   2. Click el toggle "Active" en la esquina superior derecha
   3. Confirma la activación
   ```

2. **Verificar Activación**
   - El workflow debe mostrar estado "Active"
   - El formulario web debe estar disponible

## 🧪 Pruebas de Funcionamiento

### Prueba 1: Verificar Formulario Web

1. **Obtener URL del formulario**
   ```bash
   # En n8n:
   1. Abre "TF_Main"
   2. Click en el nodo "Formulario"
   3. Copia la URL del webhook
   ```

2. **Probar formulario**
   - Abre la URL en tu navegador
   - Verifica que se muestre el formulario
   - Prueba subir un archivo de prueba

### Prueba 2: Ejecutar Workflow Completo

1. **Preparar archivo de prueba**
   - Crea un CV de prueba en PDF o imagen
   - Asegúrate de que tenga texto legible

2. **Ejecutar prueba**
   - Sube el CV a través del formulario
   - Proporciona un email válido
   - Monitorea la ejecución en n8n

3. **Verificar resultados**
   - Revisa los logs de ejecución
   - Verifica que se reciba el email
   - Comprueba que el contenido sea correcto

## 🔍 Solución de Problemas

### Error: "Credential not found"

**Síntomas:**
- El workflow falla con error de credenciales
- Los nodos muestran "Credential not found"

**Solución:**
```bash
1. Verifica que todas las credenciales estén creadas
2. Asegúrate de que los nombres coincidan exactamente:
   - "Mistral Cloud account"
   - "OpenAi account" 
   - "Header RapidAPI- JSearch"
   - "Gmail account"
3. Revisa que las API keys sean válidas
```

### Error: "Workflow not found"

**Síntomas:**
- Error al ejecutar el subworkflow
- "Workflow not found" en los logs

**Solución:**
```bash
1. Verifica que ambos workflows estén importados
2. Asegúrate de que el ID del subworkflow sea correcto
3. Revisa la configuración del nodo "Execute Workflow"
```

### Error: "API rate limit exceeded"

**Síntomas:**
- Errores de límite de API
- Workflow se detiene en nodos de API

**Solución:**
```bash
1. Verifica los límites de tu plan de API
2. Considera actualizar a un plan de pago
3. Implementa delays entre llamadas si es necesario
```

### Error: "File format not supported"

**Síntomas:**
- Error al procesar archivos
- El switch no reconoce el tipo de archivo

**Solución:**
```bash
1. Verifica que el archivo sea PDF, PNG o JPG
2. Asegúrate de que el archivo no esté corrupto
3. Revisa la configuración del nodo Switch
```

## 📊 Monitoreo y Mantenimiento

### Verificar Estado del Sistema

1. **Dashboard de n8n**
   - Revisa ejecuciones recientes
   - Monitorea errores y advertencias
   - Verifica uso de recursos

2. **Logs de APIs**
   - Revisa uso de cuotas en cada servicio
   - Monitorea costos de API
   - Verifica límites de rate limiting

### Mantenimiento Regular

1. **Actualizaciones de credenciales**
   - Renueva API keys periódicamente
   - Verifica que las credenciales sigan siendo válidas

2. **Optimización de costos**
   - Monitorea uso de APIs de pago
   - Ajusta límites según necesidad
   - Considera planes más económicos

## 🆘 Soporte

### Recursos de Ayuda

1. **Documentación de n8n**
   - [https://docs.n8n.io/](https://docs.n8n.io/)

2. **Comunidad n8n**
   - [https://community.n8n.io/](https://community.n8n.io/)

3. **Documentación de APIs**
   - Mistral AI: [https://docs.mistral.ai/](https://docs.mistral.ai/)
   - OpenAI: [https://platform.openai.com/docs](https://platform.openai.com/docs)
   - RapidAPI: [https://docs.rapidapi.com/](https://docs.rapidapi.com/)

### Contacto

Para soporte específico de este proyecto:
- Revisa los logs de ejecución
- Consulta la documentación del README
- Verifica la configuración paso a paso

---

**¡Instalación completada!** 🎉

Tu sistema de análisis de CV está listo para usar. Recuerda probar el flujo completo antes de ponerlo en producción.
