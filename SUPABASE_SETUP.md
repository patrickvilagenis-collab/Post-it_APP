# Sincronización en la nube con Supabase

La app guarda en `localStorage` (modo local) y, si configuras Supabase, además
**sincroniza las notas entre todos tus dispositivos en tiempo real**.

## 1. Crea un proyecto en Supabase

1. Entra en https://supabase.com y crea una cuenta gratuita.
2. **New project** → elige nombre, contraseña y región. Espera a que termine de aprovisionarse (~1 min).

## 2. Crea la tabla `notes`

En el panel de Supabase ve a **SQL Editor → New query**, pega esto y pulsa **Run**:

```sql
create table public.notes (
  id          text primary key,
  board_id    text not null,
  text        text default '',
  color       text,
  x           double precision,
  y           double precision,
  rot         double precision,
  done        boolean default false,
  updated_at  timestamptz default now()
);

create index notes_board_id_idx on public.notes (board_id);

-- Seguridad: activamos RLS y permitimos acceso con la clave anónima.
-- (No hay login; el "board_id" del enlace actúa como clave del tablero.)
alter table public.notes enable row level security;

create policy "acceso anon a notes"
  on public.notes for all
  to anon
  using (true) with check (true);

-- Activa la sincronización en tiempo real para esta tabla.
alter publication supabase_realtime add table public.notes;
```

## 3. Copia tus credenciales

En **Project Settings → API** copia:

- **Project URL**
- **Project API keys → `anon` `public`**

Pégalas en `config.js`:

```js
window.SUPABASE_URL = "https://TU-PROYECTO.supabase.co";
window.SUPABASE_ANON_KEY = "ey...tu-clave-anon...";
```

> La clave `anon` es pública por diseño y es seguro publicarla; queda protegida
> por las políticas RLS de arriba.

## 4. Usa el mismo tablero en varios dispositivos

- En la cabecera, el indicador muestra **☁ Sincronizado** cuando la nube está activa
  (o **● Local** si no hay configuración).
- Pulsa **Compartir** para copiar el enlace de tu tablero (incluye `#board=...`).
- Abre ese mismo enlace en el móvil, la tablet u otro ordenador: verás y editarás
  las mismas notas, y los cambios aparecen en tiempo real.

## Notas de seguridad

- El acceso a un tablero depende de conocer su `board_id` (va en el enlace). Trátalo
  como un enlace privado: quien lo tenga puede ver y editar ese tablero.
- Si quieres aislamiento por usuario real (login), habría que añadir Supabase Auth
  y políticas RLS por `auth.uid()`. Puedo ayudarte a hacerlo si lo necesitas.
