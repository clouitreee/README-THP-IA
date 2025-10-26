Preparado para: Fundador, Tech Hilfe Pro (Kleingewerbe)
Preparado por: Consultor de Negocio MSP Europa

1. Visión y Fundamentos: El MSP "Lean"

Tu estatus de Kleingewerbeschein no es una limitación; es tu ventaja estratégica. Te permite ser ágil, personal y, gracias a tu stack tecnológico (n8n, Stripe), increíblemente eficiente.

Tu web será tu único comercial 24/7 y tu principal agente de soporte Nivel 1. El branding de "Confianza Eficiente" (FinTech-Style) se mantiene, pero con un enfoque en la automatización inteligente como diferenciador.

Branding: "Tech Hilfe Pro" es perfecto. Mantenemos el concepto visual (azul cobalto, acento verde eléctrico) y la tipografía (Inter/Satoshi).

Backbone Financiero:

Banco: Holvi (ideal para Kleingewerbe en Alemania, separa perfectamente los gastos/ingresos).

Pagos: Stripe (será el motor único para suscripciones B2C y B2B y facturación).

Tu "Superpoder": n8n autoalojado. Esta es tu arma secreta. Te permite conectar todo sin costes de suscripción de Make/Zapier, permitiendo a un solo propietario (tú) operar con la eficiencia de un equipo de 5.

2. El Núcleo: Paquetes de Precios y Onboarding

El visitante debe poder auto-segmentarse y comprar (B2C) o agendar (B2B) en menos de 90 segundos. La claridad aquí es el 90% de la conversión.

Importante (Facturación Kleingewerbe): Tu integración de Stripe debe configurarse para no cobrar IVA (Umsatzsteuer) y añadir la frase legal Gemäß § 19 UStG wird keine Umsatzsteuer berechnet. en todas las facturas.

A. Paquetes para Particulares y Familias (B2C)

El objetivo es la conversión directa online vía Stripe.

Paquete

Basis

Schutz (Protección)

Sorglos (Sin Preocupaciones)

Precio/Mes

9 €

19 €

29 €

Soporte Telefónico y Remoto

✅ (Acceso)

✅ (Prioritario)

✅ (Prioritario VIP)

Facturación Intervención

Pago por Incidente

Pago por Incidente

1x Intervención Remota (30min) / mes

Antivirus Gestionado (1 Lic.)

-

✅ (Bitdefender/ESET)

✅ (Bitdefender/ESET)

Backup en la Nube (Gestionado)

-

100 GB (Backup de Documentos)

500 GB (Backup Completo)

Chequeo Anual Remoto

-

✅ (PC "Frühjahrsputz")

✅ (Proactivo, trimestral)

Gestión de Controles Parentales

-

-

✅

Descuento Visita Domicilio

0%

10%

15%

Contratación

Botón "Contratar Ahora" (Stripe)

Botón "Contratar Ahora" (Stripe)

Botón "Contratar Ahora" (Stripe)

B. Paquetes para PYMEs y Kleingewerbe (B2B)

Basados en servicios MSP líderes (tipo NinjaOne), adaptados a PYMEs. El objetivo es "Agendar Auditoría".

Paquete

Core Monitor (Monitorización)

Managed Secure (Gestión)

Strategic Partner (Estratégico)

Enfoque

"Sabemos si algo falla"

"Evitamos que algo falle"

"Optimizamos tu negocio"

Monitorización RMM 24/7

✅

✅

✅

Gestión de Parches (SO/Apps)

✅

✅

✅

Helpdesk (Ticket/Email)

✅

✅ (Prioritario)

✅ (Prioritario + Canal Slack)

Antivirus Gestionado (EDR)

✅

✅ (Avanzado - EDR)

✅ (Avanzado - EDR)

Backup M365 / Google W.

-

✅ (1x/día)

✅ (Múltiples/día)

Backup Servidor/NAS (Local)

-

✅

✅

Formación Ciberseguridad

-

✅ (Anual)

✅ (Trimestral + Phishing Sim.)

Consultoría vCIO / Estrategia

-

-

✅ (Trimestral)

Gestión On/Offboarding

-

-

✅

Reportes (GDPR/Compliance)

-

-

✅

CTA

Botón "Agendar Consulta"

Botón "Agendar Consulta"

Botón "Agendar Consulta"

3. Roadmap por Fases (Kleingewerbe Edition)

Fase 1: MVP – Lanzamiento y Validación (Meses 1-3)

Objetivo: Validar los paquetes B2C, capturar los primeros 10 clientes B2B (para auditoría) y establecer la marca. Lean startup total.

Stack Tecnológico (Recomendación):

Plataforma: Framer.

Por qué: Máxima velocidad de lanzamiento. Diseño 2025, animaciones (typewriting, scroll reveal) nativas. Te permite lanzar en 1-2 semanas.

Pagos B2C: Stripe Payment Links. (Simple, rápido. Un link por cada plan B2C).

Agendar B2B: Calendly (versión gratuita o básica).

Chat: Tidio o Crisp (Plan Gratuito).

Automatización: Tu n8n autoalojado.

Páginas y Estructura Clave:

Home: Hero (con typewriting), segmentación B2C/B2B inmediata.

Servicios Particulares (B2C): La tabla de precios de 3 niveles (arriba). Cada CTA es un Stripe Payment Link.

Servicios Empresariales (B2B): La tabla de precios de 3 niveles (arriba). Cada CTA lleva a tu Calendly.

Lead Magnet (v1): Un PDF simple: "Checklist: 10 Puntos de Seguridad GDPR para Kleingewerbe".

Acerca de / Contacto.

Automatizaciones (n8n) en MVP:

Onboarding B2C: [Stripe Pago Exitoso (Webhook)] -> [n8n] -> [Enviar Email Bienvenida con instrucciones] -> [Crear cliente en tu Google Sheet/Notion] -> [Notificación a tu Telegram].

Onboarding B2B: [Calendly Cita Agendada (Webhook)] -> [n8n] -> [Crear lead en Google Sheet/Notion] -> [Enviar Email de Confirmación al cliente].

Presupuesto Orientativo: €1.500 - €4.000 (Diseño/desarrollo en Framer. Ahorras mucho al usar n8n en lugar de Zapier y Payment Links en lugar de una integración de Billing compleja).

Fase 2: Escala – Portal y Autoridad (Meses 4-9)

Objetivo: Construir autoridad (SEO), automatizar el B2B y lanzar el Portal de Cliente v1.

Stack Tecnológico (Recomendación):

Web de Marketing: Migrar a Next.js + Tailwind CSS + Vercel.

CMS (Blog): Sanity.io (Headless, perfecto para Next.js y para alimentar al chatbot).

Portal de Cliente (v1): Desarrollo custom en subdominio (portal.techhilfe.pro) con Next.js + Supabase (para Base de Datos y Autenticación).

Pagos B2B/B2C: Integración completa de Stripe Billing & Subscriptions.

Chatbot: Botpress (autoalojado, se conecta a Sanity y a tu n8n).

Nuevas Funcionalidades y Estrategia:

Portal de Cliente (v1):

Login seguro (B2C y B2B).

Dashboard simple: "Mis Servicios", "Mis Tickets", "Facturas" (link al Stripe Customer Portal).

Formulario "Abrir Ticket" (se conecta a tu n8n).

Estrategia SEO:

Blog con artículos pilar: "Guía NIS2 para PYMEs Alemanas", "Backup M365: ¿Por qué es crucial?", "Teletrabajo seguro (Home-Office)".

Lead Magnets (Avanzados):

Calculadora Interactiva: (Next.js) "¿Cuánto te cuesta tu IT reactivo?".

Diagnóstico de Seguridad: (Typeform/Tally) que da un "score" de riesgo.

Automatizaciones (n8n) en Escala:

Ticketing: [Formulario Portal (Webhook)] -> [n8n] -> [Crear Ticket en Freshdesk/Jira (o Supabase mismo)] -> [Enviar confirmación al cliente].

Entrega Lead Magnet: [Formulario Web (Webhook)] -> [n8n] -> [Enviar PDF por email] -> [Añadir lead a Brevo/Sendinblue].

Presupuesto Orientativo: €8.000 - €20.000 (para el desarrollo del portal custom y la migración a Next.js).

Fase 3: Madurez – Hiper-Segmentación (Mes 10+)

Objetivo: Optimizar la conversión B2B con personalización. Maximizar el LTV.

Stack Tecnológico (Optimización):

Stack: Full Next.js (Web + Portal).

RMM/PSA: Selección e integración API de tu herramienta MSP (Ej: NinjaOne, Atera, Datto).

Nuevas Funcionalidades y Estrategia:

Landing Pages Sectoriales: "IT para Arztpraxen (Consultorios Médicos)", "IT para Anwälte (Abogados)", "IT para Handwerker (Artesanos)".

Portal de Cliente (v2 - Integración Total):

Conexión vía API a tu RMM.

Dashboard Visual: "Estado de Endpoints", "Último Backup", "Tickets Resueltos".

Centro de Confianza: Página visible con sellos GDPR / NIS2 y explicación sencilla de cómo proteges los datos.

Automatizaciones (n8n) en Madurez (El "Wow-Factor"):

Alertas Proactivas: [RMM Alerta (Webhook)] -> [n8n] -> [Crear Ticket Automático] -> [n8n informa al cliente en el Portal: "Hemos detectado un problema en PC-05 y ya estamos trabajando en ello."].

Onboarding B2B Completo: [Stripe Suscripción Creada (Webhook)] -> [n8n] -> [Crear cliente en RMM] -> [Crear cliente en Helpdesk] -> [Crear usuario en Portal] -> [Asignar licencias M365] -> [Enviar email de bienvenida con credenciales].

Presupuesto Orientativo: €15.000+ (para las integraciones API profundas con el RMM).

4. Tu Superpoder: Ideas de Automatización con n8n

Tu n8n autoalojado es lo que te permite competir con MSPs 10x más grandes.

Automatizaciones Internas (Eficiencia):

Triaje de Tickets: Analiza el email/formulario del ticket. Si contiene "factura" o "pago", lo etiqueta como "Facturación" y lo envía a billing@. Si contiene "urgente" o "servidor caído", envía una alerta a tu Telegram/Slack.

Gestión de Finanzas: [Nuevo extracto bancario en Holvi (Email/API)] -> [n8n] -> [Compara con facturas de Stripe] -> [Actualiza estado de pago en tu Google Sheet/Notion].

Onboarding de Clientes: (Ver Fase 3). El Zero-Touch Onboarding es tu objetivo.

Automatizaciones Externas (Valor para el Cliente):

Reportes Proactivos: [n8n (programado cada 1º de mes)] -> [Llama a la API de tu RMM y Helpdesk] -> [Genera un PDF simple con "Tickets abiertos/cerrados", "Estado de Backups", "Amenazas bloqueadas"] -> [Envía el email al cliente B2B].

Asistente de Portal: El cliente entra al portal y escribe en el chatbot (Botpress) "Quiero resetear mi contraseña de M365". [Botpress (Webhook)] -> [n8n] -> [Llama a la API de M365] -> [Inicia el flujo de reseteo y notifica al usuario].

Notificaciones de Mantenimiento: [n8n (programado)] -> [Lee tu Calendly/Google Calendar "Ventana de Mantenimiento"] -> [Envía email a clientes B2B afectados: "Recordatorio: Mañana a las 22:00..."].

5. Errores Frecuentes (A Evitar)

Ignorar el estatus Kleingewerbe: ¡Es vital! No cobrar IVA y poner la coletilla legal en las facturas de Stripe es una obligación (Gemäß § 19 UStG...).

Sobre-ingeniería del MVP: No intentes construir el portal de Fase 3 en el Mes 1. Valida los paquetes B2C con Framer y Stripe Payment Links. El flujo de caja inicial es más importante que un portal perfecto.

Precios B2B Opacos: El "Contacta para un presupuesto" frena. Las tablas de 3 niveles que has definido (Core, Managed, Strategic) son el benchmark europeo. Dan un ancla de valor.

Fotos de Stock Genéricas: Evítalas. Generan desconfianza. Usa ilustraciones de marca (tipo FinTech) o fotos reales tuyas (genera confianza local).

Un Flow B2C/B2B Mezclado: El B2C quiere un botón de "Comprar Ahora". El B2B quiere un botón de "Agendar Auditoría". Tu web debe separarlos en el hero de la Home.
