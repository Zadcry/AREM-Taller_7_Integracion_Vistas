# 📄 Informe Técnico del Taller

## 🔖 Nombre del Taller
_Taller 7 - Integración de Vistas de Arquitectura_

## 👥 Integrantes del equipo
- Santiago Andrés Araque Alfonso
- Juan Jose Forero Peña
- Julian Mauricio Zafra Moreno

## 🧠 Descripción general del trabajo
El presente trabajo tuvo como objetivo principal integrar y articular las diversas vistas arquitectónicas (negocio, información, aplicaciones, infraestructura y seguridad) desarrolladas durante el curso para el proyecto THEGEEKHUB. Se buscó construir una narrativa visual coherente que evidencie cómo las interacciones de los clientes en redes sociales y plataformas externas se conectan tecnológicamente hasta llegar a la persistencia de datos segura y escalable que exige un modelo de comercio electrónico formal.

## 🔧 Proceso de desarrollo
Para llevar a cabo el trabajo, partimos del diagrama de arquitectura previamente consolidado para THEGEEKHUB. 
1. Identificación de capas: Comenzamos separando las decisiones tecnológicas en 5 grandes bloques interconectados (Negocio, Información, Aplicaciones, Infraestructura y Seguridad).
2. Conexión de los flujos: Modelamos cómo una petición de venta, proveniente de canales externos como Instagram o Facebook, atraviesa el API Gateway, se encola asíncronamente a través de una cola de eventos y es procesada por los servicios transaccionales.
3. Mapeo de datos e infraestructura: Relacionamos las entidades del negocio (Ventas, Referencias, Clientes) directamente con su estrategia de almacenamiento segregado (Base de Datos Relacional Central para transacciones ACID e Historial NoSQL para auditoría) dentro de un entorno de microservicios.
4. Validación de Seguridad e Integración: Por último, cruzamos esta arquitectura con los controles definidos previamente en la matriz STRIDE y normatividad, garantizando la existencia de roles para el dashboard de socios y el control estricto del acceso. Se utilizó draw.io como herramienta gráfica para trazar y unificar todas estas relaciones.

## 🧩 Análisis del modelo propuesto
- Cómo se estructura el modelo entregado: El modelo se consolida como un mapa integral. En la parte de interacción externa se ubica la vista de negocio, cosas como canales sociales y dashboard administrativo, conectada a una capa de orquestación, la cual contiene el API Gateway y Cola de eventos. En el núcleo operan los dominios de la aplicación (Servicio de Ventas/Tracking Financiero), los cuales persisten datos en infraestructuras específicas (Relacional y NoSQL) garantizando alta disponibilidad. En todo momento, se asume la aplicación de las políticas de seguridad.
- Cómo representa las necesidades del cliente: El modelo aborda directamente los cuellos de botella de THEGEEKHUB, eliminando la gestión manual en hojas de Excel. Esto asegura la consistencia de inventario en tiempo real, estandariza la creación de SKUs y protege la información financiera al integrarse de manera segura con pasarelas de pago.
- Qué supuestos se tomaron: Se asume que THEGEEKHUB desplegará estos servicios en una infraestructura nativa de la nube con capacidad de crecimiento elástico. Adicionalmente, se da por hecho que el proceso de autenticación financiera y validación de cobros se delegará completamente a los tokens seguros de MercadoPago o Nequi, sin almacenar datos sensibles de tarjetas de crédito localmente para reducir responsabilidades normativas.

## 📈 Diagrama final entregado
<img width="4135" height="1055" alt="tablero-integrado-cliente drawio" src="https://github.com/user-attachments/assets/9e38b011-780b-4362-accd-b8be565b534c" />

## 📋 Tabla de actores, entidades o componentes (si aplica)

| Nombre del elemento | Tipo | Descripción | Responsable |
|---------------------|------|-------------|-------------|
| Comprador | Actor (Negocio) | Cliente que realiza solicitudes de compra mediante redes sociales. | THEGEEKHUB / Cliente |
| Canales Externos | Componente (Aplicación) | Interfaces en Instagram, Facebook o MercadoLibre. | Plataformas de 3ros |
| API Gateway / Controlador | Componente (Aplicación) | Punto de entrada unificado y validador de ventas externas. | Equipo TI de THEGEEKHUB |
| Servicio de Ventas y Referencias | Componente (Microservicio) | Lógica central para gestión de inventario, SKU y pedidos. | Equipo TI de THEGEEKHUB |
| Servicio de Tracking Financiero | Componente (Microservicio) | Encargado de sincronizar pagos y manejar la lógica de retiros. | Equipo TI de THEGEEKHUB |
| BD Relacional Central | Entidad (Datos/Infra) | Persistencia transaccional consistente para ventas y clientes. | Arquitecto de Datos |
| Historial NoSQL | Entidad (Datos/Infra) | Almacenamiento de alto volumen para logs transaccionales. | Arquitecto de Datos |
| Controles STRIDE / RBAC | Seguridad | Reglas de control de acceso para el dashboard administrativo. | Oficial de Seguridad |

## 🔍 Investigación complementaria
### Tema investigado: 
Estándares y Modelos para la Descripción e Integración de Vistas Arquitectónicas

### Resumen:
La representación de sistemas complejos requiere abstraer diferentes áreas de interés para distintos perfiles de partes interesadas, lo que hace metodológicamente imposible utilizar un único modelo. Para estructurar esta multiplicidad, el estándar internacional ISO/IEC/IEEE 42010 establece las bases normativas para la descripción de arquitecturas de sistemas y software. Este marco determina que una arquitectura debe documentarse mediante múltiples "vistas", cada una gobernada por un "punto de vista" específico. El aspecto más crítico que introduce el estándar para la integración es la definición formal de "correspondencias" y "reglas de correspondencia", mecanismos que aseguran que las diferentes vistas no actúen como silos aislados, sino como dimensiones consistentes que se interconectan, validan y no se contradicen entre sí.

Un referente clásico que materializa esta necesidad de integración es el Modelo de Vistas 4+1, propuesto por Philippe Kruchten. Este modelo organiza el sistema en cuatro perspectivas fundamentales: Lógica (datos y entidades), Procesos (concurrencia y comportamiento), Desarrollo (componentes de software) y Física (topología de despliegue e infraestructura). La verdadera innovación para la integración en este modelo radica en el "+1", que representa los Casos de Uso o Escenarios. Estos escenarios actúan como el hilo conductor o amalgama que enlaza de manera transversal las cuatro vistas estáticas, demostrando dinámica y visualmente cómo la infraestructura, las bases de datos y las aplicaciones colaboran en sincronía para ejecutar un proceso específico.

Finalmente, la integración de vistas arquitectónicas persigue como fin último garantizar la trazabilidad total y el alineamiento sistémico. Cuando las capas (negocio, información, aplicaciones e infraestructura) se articulan de manera cohesiva, es posible realizar análisis de impacto precisos. Por ejemplo, permite comprender topológicamente cómo la modificación de un control de seguridad afecta simultáneamente la lógica de un microservicio y la configuración de una red física. Esta consolidación holística facilita la comunicación efectiva entre ingenieros, arquitectos y directivos, certificando que los despliegues tecnológicos respondan milimétricamente a los objetivos estructurales del diseño.

## 📚 Referencias
- [1] ISO/IEC/IEEE. ISO/IEC/IEEE 42010:2011 - Systems and software engineering — Architecture description. 2011. https://www.iso.org/standard/50508.html
- [2] Kruchten, Philippe. Architectural Blueprints—The "4+1" View Model of Software Architecture. IEEE Software 12, no. 6 (1995): 42-50.

---

_Este documento hace parte de la entrega del taller 7 del curso AREM (Arquitectura Empresarial) - Universidad de La Sabana._
