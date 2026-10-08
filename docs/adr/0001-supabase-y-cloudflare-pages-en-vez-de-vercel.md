# Supabase para todo el backend y Cloudflare Pages para el frontend, no Vercel

El sistema se hostea gratis: la app React (estática) en Cloudflare Pages y todo lo del lado del servidor en Supabase (PostgreSQL con RLS, Auth, funciones SQL transaccionales, pg_cron para las tareas programadas, pg_net + Edge Functions para PDF y mails, Storage para los PDF). La propuesta inicial era Vercel, pero su plan gratuito (Hobby) es solo para uso personal no comercial, y este es un trabajo pago para un cliente; además, sus cron corren como mucho una vez por día con ±59 minutos de imprecisión.

## Consecuencias

- Tener los cron dentro de la base (pg_cron) mantiene la actividad que evita que Supabase pause el proyecto gratuito tras 7 días sin uso.
- El respaldo de la base no depende de Supabase: un workflow programado de GitHub Actions exporta una copia cifrada, por eso el repositorio tiene que ser privado.
- Las cuentas de los servicios pertenecen al Taller (con un mail del Taller) y la desarrolladora es miembro invitado.
