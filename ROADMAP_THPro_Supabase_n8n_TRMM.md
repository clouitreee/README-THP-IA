# Tech Hilfe Pro · Infra MSP · Supabase + n8n + TRMM

> Objetivo: orquestación segura con túneles, RLS, automatizaciones n8n, backups con retención y observabilidad saneada. Nada expuesto a lo bruto.

## 🧭 Fases

1. **DNS & Túneles** (Cloudflare)
   - Crear subdominios: `api.techhilfepro.de`, `studio.techhilfepro.de`, `n8n.techhilfepro.de`.
   - Ingress en `cloudflared`:
     - `api.*` → servicio Supabase REST/Kong interno.
     - `studio.*` → Supabase Studio (solo IPs/Zero Trust).
     - `n8n.*` → n8n:5678 con WebSockets OK.
   - Cerrar cualquier exposición directa de 5432/8000/3000.

2. **SMTP / Auth**
   - En `.env` de Supabase: `SMTP_HOST`, `SMTP_PORT`, `SMTP_USER`, `SMTP_PASS`, `SMTP_ADMIN_EMAIL`, `SMTP_SENDER_NAME`.
   - Verificar envío de confirmación y reset en GoTrue.

3. **Modelado de datos (MVP)**
   - Esquemas/tablas: `clientes`, `sitios`, `dispositivos`, `tickets`, `contratos`, `suscripciones`, `eventos_rmm`, `users`.
   - Vistas: `v_dispositivos_sin_parchear`, `v_tickets_sla_vencidos`, `v_clientes_mrr`.

4. **Seguridad**
   - RLS por tenant desde el día 1.
   - Roles: `anon` lectura pública mínima, `service_role` para automatizaciones, `admin` auditoría.
   - Zero Trust para Studio y n8n admin.

5. **Automatización n8n (v1)**
   - Backup DB nocturno → `/opt/supabase/backups/YYYY/MM/` y espejo S3/NAS.
   - Onboarding cliente: alta + usuario + email + ticket inicial.
   - Ingesta TRMM: webhook → `eventos_rmm` → ticket crítico.
   - Facturación ligera: cambios en `suscripciones` → payload pasarela.

6. **Backups & Retención**
   - Política: 7 diarias, 4 semanales, 6 mensuales.
   - Prueba de restauración mensual en `staging`.
   - Healthcheck de inicio/fin de backup.

7. **Observabilidad**
   - Uptime Kuma: monitores `api.*`, `studio.*`, `n8n.*`.
   - Alertas ntfy/Telegram a fallo de healthcheck o backup.

8. **TRMM convivencia**
   - Reservar 80/443 para TRMM.
   - Si NATS standard: abrir 4222/TCP.
   - Agentes siempre salientes por 443 hacia tus dominios.

9. **Actualizaciones & Rollback**
   - `docker compose pull && up -d`, verificación, si falla → rollback a imágenes previas y `.env` anterior.
   - Etiquetar releases infra.

10. **Escalado**
   - Migrar a Swarm/k3s cuando toque.
   - Separar Postgres en host o instancia dedicada.

---

## 🧩 Diagrama lógico (final esperado)

Internet
  │
  │  [Cloudflare]
  │   ┌────────────────────────────────────────────────────────┐
  │   │ DNS + Zero Trust + Túneles                            │
  │   │  api.techhilfepro.de  → cloudflared →  http://supabase-kong:8000
  │   │  studio.techhilfepro.de → cloudflared → http://studio:3000 (ZT/IP allow)
  │   │  n8n.techhilfepro.de   → cloudflared → http://n8n:5678 (WS)         │
  │   └────────────────────────────────────────────────────────┘
  │
Server (Docker)
┌────────────────────────────────────────────────────────────────────────────┐
│                             Docker network: supanet                         │
│  ┌───────────────┐   ┌───────────┐   ┌──────────┐   ┌─────────────┐        │
│  │ cloudflared   │   │ kong(REST)│   │ studio   │   │ n8n (5678)  │        │
│  └─────▲─────────┘   └────▲──────┘   └────▲─────┘   └──────▲──────┘        │
│        │                  │               │               │                │
│        │          ┌───────┴────────┐      │               │                │
│        │          │ supabase suite │      │               │                │
│        │          │ (auth,rest,    │      │               │                │
│        │          │ realtime,      │      │               │                │
│        │          │ storage, etc.) │      │               │                │
│        │          └───────▲────────┘      │               │                │
│                ┌──────────┴──────┐        │               │                │
│                │ postgres (5432) │◄───────┘        ┌──────┴───────┐        │
│                │  /var/lib/pg    │                 │ uptime-kuma  │        │
│                └────────▲────────┘                 └──────▲───────┘        │
│                         │        ┌─────────────────────────┴─────────────┐  │
│                   backups cron   │   /opt/supabase/backups + S3/NAS      │  │
│                         │        └───────────────────────────────────────┘  │
└────────────────────────────────────────────────────────────────────────────┘

---

## 🔐 Variables críticas

- Supabase: `JWT_SECRET`, `ANON_KEY`, `SERVICE_ROLE_KEY`
- SMTP: `SMTP_HOST`, `SMTP_PORT`, `SMTP_USER`, `SMTP_PASS`, `SMTP_ADMIN_EMAIL`, `SMTP_SENDER_NAME`
- n8n: `N8N_HOST`, `N8N_PORT`, `WEBHOOK_URL`, `N8N_ENCRYPTION_KEY`
- Cloudflare: credenciales de `cloudflared` (token de túnel)
- TRMM: dominios/puertos y, si aplica, `NATS` 4222

---

## ✅ Checklist de “no volver a tropezar”
- [ ] Nada expuesto directamente (5432/3000/8000) fuera del túnel.
- [ ] RLS activo antes de cargar datos reales.
- [ ] SMTP probado con confirmación y reset.
- [ ] Backups con retención + prueba de restore.
- [ ] Uptime Kuma con alertas.
- [ ] Reglas ingress revisadas después de cada cambio.
