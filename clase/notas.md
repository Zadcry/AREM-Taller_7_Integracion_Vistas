# 🗒️ Registro de Trabajo en Clase - Taller 7

## 📆 Fecha de la sesión
22/05/2026

## 👥 Integrantes presentes
- Santiago Andrés Araque Alfonso
- Juan Jose Forero Peña
- Julian Mauricio Zafra Moreno

## 🧠 Actividades realizadas en clase

Durante la sesión se trabajó en la integración de las vistas arquitectónicas del caso FarmApp, una cadena nacional de farmacias con plataforma de e-commerce integrada.

### Actividades desarrolladas

- Se analizaron los procesos de negocio relacionados con compras en línea, pagos digitales, validación de prescripciones y despacho de pedidos.
- Se identificaron las entidades principales del sistema como Cliente, Producto, Pedido, Inventario, Pago y Descuento.
- Se discutió la integración entre aplicaciones como App móvil, plataforma e-commerce, CRM, POS y sistema logístico.
- Se definió una infraestructura híbrida con servidores regionales, nube híbrida y bases de datos replicadas.
- Se establecieron mecanismos de seguridad como cifrado de datos, control de acceso por roles y monitoreo de fraude.
- Se organizó la relación entre las diferentes vistas arquitectónicas para garantizar trazabilidad y coherencia del modelo.

### Herramientas utilizadas

- Draw.io
- Bocetos iniciales en Papel


### Avance alcanzado

- Identificación de actores y procesos principales.
- Definición de entidades y relaciones de información.
- Estructuración de las aplicaciones involucradas.
- Diseño preliminar de infraestructura y seguridad.
- Organización de la arquitectura empresarial integrada.

---

# 📌 Información del Caso FarmApp

## 1. Vista de Negocio

### Procesos principales

| Proceso | Descripción | Actores involucrados |
|---|---|---|
| Compra de medicamentos | El cliente realiza pedidos desde la app/web o en tienda física | Cliente, sistema e-commerce, POS |
| Validación de prescripción | Verificación de fórmulas médicas para medicamentos controlados | Cliente, farmacéutico |
| Gestión de inventario | Sincronización de existencias entre tiendas y bodegas | Inventario, logística |
| Pago electrónico | Procesamiento de pagos digitales y validación de transacciones | Pasarela de pago, banco |
| Despacho y entrega | Preparación y envío de pedidos a domicilio | Logística, repartidores |
| Promociones personalizadas | Aplicación de descuentos según historial y perfil del cliente | CRM, motor de promociones |
| Seguimiento del pedido | Rastreo en tiempo real del estado del envío | Cliente, logística |

### Objetivos del negocio

- Mejorar la experiencia de compra digital y presencial.
- Mantener disponibilidad sincronizada de productos.
- Reducir tiempos de entrega.
- Personalizar promociones y recomendaciones.
- Garantizar seguridad de datos y transacciones.

---

## 2. Vista de Información

### Entidades principales

| Entidad | Descripción | Relación |
|---|---|---|
| Cliente | Información personal y preferencias del usuario | Realiza pedidos |
| Pedido | Registro de compras realizadas | Contiene productos |
| Producto | Medicamentos y artículos disponibles | Asociado al inventario |
| Inventario | Cantidad disponible por sucursal | Actualiza disponibilidad |
| Descuento | Promociones y cupones aplicados | Asociado al cliente o pedido |
| Prescripción | Fórmula médica digital o física | Validada por farmacia |
| Pago | Información de transacciones | Relacionado con pedido |
| Entrega | Datos logísticos y estado del envío | Asociado al pedido |

### Flujo de información

1. El cliente realiza un pedido.
2. El sistema consulta inventario disponible.
3. Se valida la prescripción si aplica.
4. El CRM identifica promociones personalizadas.
5. Se procesa el pago.
6. El sistema genera orden de despacho.
7. Logística actualiza el estado de entrega.
8. El historial queda almacenado en el CRM.

---

## 3. Vista de Aplicaciones

### Sistemas involucrados

| Aplicación | Función |
|---|---|
| App móvil | Permite compras, rastreo y promociones |
| Plataforma E-commerce | Gestión web de pedidos y catálogo |
| Sistema POS | Ventas y sincronización en tiendas físicas |
| CRM | Gestión de clientes y campañas |
| Sistema de Inventario | Control de stock en tiempo real |
| Pasarela de Pago | Procesamiento de pagos electrónicos |
| Sistema Logístico | Gestión de despachos y entregas |
| Servicio de Notificaciones | Envío de correos, SMS y push |

### Integraciones principales

- App móvil ↔ E-commerce
- E-commerce ↔ Inventario
- POS ↔ Inventario
- CRM ↔ App/E-commerce
- E-commerce ↔ Pasarela de pago
- Sistema logístico ↔ Rastreo de pedidos

---

## 4. Vista de Infraestructura

### Componentes de infraestructura

| Componente | Función |
|---|---|
| Nube híbrida | Hospedaje de aplicaciones críticas |
| Servidores regionales | Reducción de latencia y continuidad operativa |
| Base de datos replicada | Alta disponibilidad y respaldo |
| Balanceadores de carga | Distribución de tráfico |
| Red VPN corporativa | Comunicación segura entre sedes |
| CDN | Optimización de contenido web |
| Centro de monitoreo | Supervisión de rendimiento y disponibilidad |

### Arquitectura tecnológica

- Frontend web y móvil en nube pública.
- Sistemas internos conectados mediante APIs.
- Bases de datos replicadas entre regiones.
- Servicios críticos desplegados con redundancia.
- Integración híbrida entre infraestructura local y cloud.

---

## 5. Vista de Seguridad

### Controles implementados

| Control | Descripción |
|---|---|
| Control de acceso por roles (RBAC) | Permisos según perfil del usuario |
| Cifrado de datos | Protección de datos personales y pagos |
| Autenticación multifactor | Seguridad adicional para usuarios administrativos |
| Monitoreo de fraude | Detección de transacciones sospechosas |
| Logs y auditoría | Registro de actividades del sistema |
| Firewall y WAF | Protección contra ataques externos |
| Backup y recuperación | Continuidad ante fallos o incidentes |

### Riesgos mitigados

- Robo de información sensible.
- Acceso no autorizado.
- Fraudes en pagos electrónicos.
- Pérdida de información crítica.
- Interrupciones del servicio.

---

## 6. Relación entre vistas arquitectónicas

| Vista | Relación |
|---|---|
| Negocio ↔ Información | Los procesos generan y consumen datos |
| Información ↔ Aplicaciones | Las aplicaciones administran entidades y transacciones |
| Aplicaciones ↔ Infraestructura | Los sistemas requieren servidores y conectividad |
| Seguridad ↔ Todas las vistas | Protege procesos, datos, aplicaciones e infraestructura |

---

## 7. Conclusión

La integración de las vistas arquitectónicas de FarmApp permite entender cómo los procesos de negocio, la gestión de datos, las aplicaciones, la infraestructura tecnológica y los controles de seguridad trabajan de forma coordinada para ofrecer una experiencia de compra eficiente, segura y escalable tanto en canales digitales como físicos.

---

## 🧩 Boceto inicial del modelo

<img width="3444" height="1414" alt="tablero-farmapp drawio" src="https://github.com/user-attachments/assets/a010e1dd-a394-46bb-a12c-d5b6906a002c" />

---

## 🔁 Tareas definidas para complementar el taller

| Tarea asignada | Responsable | Fecha estimada |
|----------------|-------------|----------------|
| Modelado final en draw.io | Santiago Andrés Araque Alfonso | 22/05 |
| Redacción del informe |  Julian Mauricio Zafra Moreno | 22/05 |
| Investigación y referencias | Juan Jose Forero Peña | 22/05 |

---

_Este documento resume el trabajo colaborativo realizado durante la sesión del taller de arquitectura empresarial aplicado al caso FarmApp._
