# QStrauss AI Agent - Request Intake Blueprint

Blueprint para importar en Workfront Fusion que crea un webhook intake para el AI Agent de QStrauss.

## 📋 Estructura del Escenario

```
[Custom Webhook] → [Router] → Ruta 1 (general) → [Workfront: Create Issue] → [Webhook Response]
                             → Ruta 2 (wf)      → [Workfront: Create Issue] → [Webhook Response]
```

## 🚀 Cómo importar

1. **Ve a Workfront Fusion** → Scenarios → **Create a new scenario**
2. Click en los **3 puntos** (menú) abajo a la izquierda → **Import Blueprint**
3. Abre el archivo `blueprint.json` y **copia TODO el contenido**
4. **Pega** el contenido en Fusion
5. Click **Save**

## ⚙️ Configuración manual (después de importar)

### 1. Webhook (Módulo 1)
- Click en el módulo del webhook
- Click **"Add"** para crear un nuevo webhook
- **Copia la URL** del webhook que te genere
- Guárdala para agregarla al `.env`

### 2. Conexión Workfront (Módulos 3 y 4)
- En cada módulo "Create Record" de Workfront
- Selecciona tu conexión existente: **qstraussptrsd**
- Selecciona el **proyecto destino** donde se crearán los Issues

### 3. Custom Forms (ya mapeados)
- **Módulo 3 (General):** Custom Form ID `6933061c000706e95fa140dbe15ccc94`
- **Módulo 4 (WF):** Custom Form ID `68e5823900050e2ee835d92814eb0778`
- Los campos ya están mapeados con la sintaxis `DE:nombre_del_campo`

### 4. Activar el escenario
- Una vez configurado todo, **activa el escenario**
- Copia la URL del webhook y agrégala a tu `.env`:

```env
FUSION_WEBHOOK_URL=https://hook.us1.make.com/tu-url-del-webhook-aqui
```

## 📊 Data Structure del Webhook

El webhook recibe este JSON:

```json
{
  "form_type": "general",
  "request": {
    "type_of_application": "Bug",
    "priority": "High",
    "client": "TechFlow",
    "related_project": "Portal TechFlow v2",
    "description_of_requirements": "...",
    "problem_or_need": "...",
    "expected_benefit": "...",
    "requires_external_integration": false,
    "external_system": "",
    "development_type": ["Workfront", "Fusion"],
    "is_new_functionality": true,
    "object_and_level": "Issue",
    "what_needs_to_be_done": "...",
    "ids_of_objects_involved": "...",
    "expected_field_values": "...",
    "event_that_triggers_the_flow": "...",
    "conditions_and_exceptions": "...",
    "necessary_permissions": "...",
    "real_example_for_testing": "...",
    "expected_technical_result": "...",
    "additional_information": "..."
  },
  "consultant_name": "María García",
  "consultant_email": "maria.garcia@qstrauss.com",
  "teams_conversation_id": "19:abc123@thread.v2",
  "submitted_at": "2026-04-01T15:30:00.000Z"
}
```

## ✅ Custom Forms

### Form General (ID: `6933061c000706e95fa140dbe15ccc94`)
- Type of Application
- Priority
- Client
- Related Project
- Description of requirements
- Problem or need that one seeks to solve
- Expected benefit
- Does it require integration with an external system?
- External system to be integrated

### Form WF (ID: `68e5823900050e2ee835d92814eb0778`)
- Development Type
- Is this a New Functionality?
- Related Project
- Additional Information
- Client
- Object and level of the field
- What needs to be done
- IDs of the objects involved
- Expected field values
- Event that triggers the flow
- Conditions and exceptions
- Necessary permissions
- Real example for testing
- Expected technical result
