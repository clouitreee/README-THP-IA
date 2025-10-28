# THP-MSP Roadmap (Infra 2025) 🚀

> Estado: Supabase + n8n autoalojados; túnel activo para n8n. Pendiente: correo/Auth, túneles para Supabase, backups, observabilidad y hardening.

## 🧭 Arquitectura objetivo (vista rápida)

Internet
  │
  ▼
Cloudflare (DNS + Zero Trust)
  │  ├─ CNAME/AAAA → Argo Tunnel (cloudflared)
  │  └─ Access (opcional) con policies por email/IP
  ▼
cloudflared @ server01
  ├─ api.techhilfepro.de   → http://127.0.0.1:8000    (Supabase API Gateway)
  ├─ studio.techhilfepro.de→ http://127.0.0.1:3000    (Supabase Studio)
  ├─ n8n.techhilfepro.de   → http://127.0.0.1:5678    (n8n)
  └─ fallback              → http_status:404
                           (sin puerto 5432 expuesto)

## 🧩 Componentes

- **Supabase (Docker Compose)**: Postgres 15+, Kong/Gateway 8000, Studio 3000, GoTrue/Auth, PostgREST.
- **n8n**: Docker + Cloudflared. ✔ Ya operativo en `n8n.techhilfepro.de`.
- **Cloudflare Tunnel**: ingress por hostname y regla catch-all 404 (última del archivo).  
- **Correo (Zoho Mail)**: SMTP `smtp.zoho.com`, 587 STARTTLS o 465 SSL, SPF/DKIM/DMARC en DNS.

## 🔐 Seguridad básica

- No exponer 5432/3000. Todo por túnel/Access.  
- `.env` con secretos fuertes (`JWT_SECRET`, `ANON_KEY`, `SERVICE_ROLE_KEY`) guardado fuera del repo; backup cifrado.  
- RLS desde el día 1 en tablas con datos de clientes.

## 🗄️ Datos (MVP)

- Tablas: `clientes`, `sitios`, `dispositivos`, `tickets`, `contratos`, `suscripciones`, `eventos_rmm`, `users`.
- Vistas: `v_dispositivos_sin_parchear`, `v_tickets_sla_vencidos`, `v_clientes_mrr`.
- RLS: lectura por tenant, escritura por técnico, auditoría admin.

## ⚙️ Automatizaciones n8n (primeras)

1) **Backup nocturno Postgres** → `/opt/supabase/backups` + espejo S3/NAS.  
2) **Onboarding cliente** → inserta en `clientes`, crea usuario Auth, email bienvenida.  
3) **Ingesta alertas RMM** → webhook → `eventos_rmm` → si crítico, abre ticket.  
4) **Facturación ligera** → cambios en `suscripciones` disparan payload a pasarela.

## 🩺 Observabilidad

- Healthchecks: `api.*`, `studio.*`, `n8n.*`.  
- Alertas: ntfy/Telegram cuando falle healthcheck o backup.

## 🧯 Backups y retención

- Diario (7 días), semanal (4), mensual (6).  
- **Restauración de prueba mensual** en base de staging.

## 🛣️ Fases del roadmap

### Fase 1 — Correo/Auth y túneles de Supabase
- [ ] Corregir DNS: eliminar/corregir TLSA `_25._tcp.<host>` con dobles puntos, si existe.
- [ ] Verificar SPF/DKIM/DMARC de `techhilfepro.de`.
- [ ] Configurar `GOTRUE_SMTP_*` con Zoho (587 STARTTLS).
- [ ] Crear hostnames `api.techhilfepro.de` y `studio.techhilfepro.de` en tunnel; añadir catch-all 404.

### Fase 2 — Backups + Observabilidad
- [ ] Job `pg_dump` + rotación; subir a S3/NAS.
- [ ] UptimeKuma/healthchecks y alertas a ntfy.

### Fase 3 — Modelado y RLS por tenant
- [ ] Migraciones SQL (tablas/vistas).
- [ ] Políticas RLS y tests.

### Fase 4 — Automatizaciones n8n
- [ ] Flujos 1–4 del MVP.
- [ ] Logs y manejo de errores.

## 🧪 Comandos de verificación (ejemplos)

### DNS/TLSA
```bash
# ¿Existe TLSA mal formado? (doble punto suele causar "invalid empty label")
dig +short TLSA _25._tcp.mail.techhilfepro.de
