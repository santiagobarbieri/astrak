# 🚀 ASTRAK - Deploy en Netlify

## ⚡ Quick Deploy (2 minutos)

### Opción 1: Drag & Drop (MÁS RÁPIDO)

1. Ve a https://netlify.com
2. Crea cuenta (si no tienes)
3. Haz clic en **"Sites"** en el menú
4. Arrastra tu carpeta `astrak-project` al área de drop
5. **¡Listo! Tu sitio está en vivo en segundos**

**URL automática:** `astrak-xxxxx.netlify.app`

---

### Opción 2: Git Connection (RECOMENDADO)

#### Paso 1: Preparar repositorio

```bash
# En tu carpeta del proyecto
git init
git add .
git commit -m "ASTRAK v2 - Netlify ready"
git remote add origin https://github.com/tu-usuario/astrak.git
git push -u origin main
```

#### Paso 2: Conectar en Netlify

1. Ve a https://netlify.com
2. Click en **"New site from Git"**
3. Elige proveedor (GitHub, GitLab, Bitbucket)
4. Selecciona el repositorio `astrak`
5. Deja todo por defecto
6. Click **"Deploy"**

**Netlify automáticamente:**
- Detecta `netlify.toml`
- No ejecuta build
- Publica los archivos
- Genera URL

---

### Opción 3: Netlify CLI (Para desarrolladores)

```bash
# Instalar CLI
npm install -g netlify-cli

# Loguear
netlify login

# Deploy
netlify deploy --prod --dir=.

# Listo!
```

---

## 📁 Estructura para Netlify

```
astrak-project/
├── index.html              ← Principal
├── netlify.toml            ← Config Netlify
├── .gitignore
├── README.md
│
└── img/
    ├── favicon.png
    └── logo.png
```

**Eso es todo.** Netlify automáticamente publica todo.

---

## ✅ Diferencias: Netlify vs Vercel

| Aspecto | Netlify | Vercel |
|---------|---------|--------|
| **Setup** | Más simple | Igual de simple |
| **Performance** | Excelente | Excelente |
| **Dominio gratuito** | ✅ netlify.app | ✅ vercel.app |
| **Build** | No necesario | No necesario |
| **Redirects** | netlify.toml | vercel.json |
| **Serverless** | ✅ Con Functions | ✅ Con Serverless |
| **Precio** | Gratis + Pro | Gratis + Pro |
| **SSL** | ✅ Automático | ✅ Automático |

**Para ASTRAK (sitio estático):** Son prácticamente idénticos.

---

## 🎯 Post-Deploy en Netlify

### Verificar que funciona

1. **Abre tu sitio** en `https://tu-dominio.netlify.app`
2. **Comprueba:**
   - Logo en header ✓
   - Logo en footer ✓
   - Favicon en pestaña ✓
   - Filtros animan ✓
   - Noticias cargan ✓
   - Clima funciona ✓

### F12 - Console (No debe haber errores)

```
✓ Sin warnings de Tailwind
✓ Sin errores de 404
✓ Sin CORS errors
```

---

## 🔄 Actualizar tu sitio

### Opción 1: Si usaste Git

```bash
# Hacer cambios locales
# Editar index.html por ejemplo

git add .
git commit -m "Update: descripción"
git push

# Netlify automáticamente redeploya en < 30 segundos
```

### Opción 2: Si usaste Drag & Drop

1. Modifica los archivos localmente
2. Ve a Netlify → Deploys
3. Click "Trigger deploy" o arrastra la carpeta de nuevo

---

## 🌐 Dominio Personalizado

### Agregar tu dominio

1. En Netlify Dashboard → Site Settings
2. Ve a "Domain Settings"
3. Click "Add domain"
4. Ingresa tu dominio (ej: astrak.com)
5. Sigue las instrucciones de DNS

**Nota:** Netlify configura SSL automáticamente en < 5 minutos

---

## 🔥 Ventajas de Netlify para ASTRAK

✅ **Zero Configuration** - No necesitas config complicada
✅ **Instant Deploy** - Tu código en vivo en segundos
✅ **Auto Rollback** - Si algo sale mal, vuelve atrás
✅ **Split Testing** - Prueba versiones simultáneamente
✅ **Analytics** - Ver datos de tu sitio
✅ **Notifications** - Alertas de deploy
✅ **Netlify Functions** - Agregar backend después si necesitas

---

## 📝 Arquivo netlify.toml - Qué hace

```toml
[build]
  command = "echo 'No build required'"
  publish = "."
```
→ No ejecuta build, publica todo

```toml
[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```
→ SPA routing (si lo necesitas)

```toml
[[headers]]
  Cache-Control = "public, max-age=3600"
```
→ Caching inteligente para performance

---

## 🚨 Troubleshooting en Netlify

### "Logo no aparece"
```
❌ Verifica: img/logo.png existe
❌ Revisa: F12 → Network → busca 404
✅ Solución: Actualiza los archivos
```

### "Noticias no cargan"
```
❌ Google News bloquea requests frecuentes
✅ Espera unos minutos
✅ Recarga (Ctrl+Shift+R hard refresh)
```

### "Clima dice 22°C siempre"
```
❌ Negaste permiso de geolocalización
✅ Abre Settings → Privacidad → Permisos de sitio
✅ Permite ubicación para el sitio
```

### "Sitio lento"
```
✅ Netlify automáticamente cachea
✅ Primera carga: ~2-3 segundos (OK)
✅ Cargas posteriores: < 1 segundo
```

---

## 📊 Monitoring en Netlify

### Dashboard
- **Builds** - Historial de deployments
- **Deploys** - Estado actual del sitio
- **Analytics** - Visitantes, origen del tráfico
- **Functions** - Si agregas backend

### Logs
1. Ve a Netlify Dashboard
2. Click en "Deploys"
3. Haz click en un deploy específico
4. Ver logs de compilación y publicación

---

## 💾 Backup de tu sitio

Todos tus archivos están en:
1. **Local** en tu computadora
2. **GitHub/GitLab** (si usaste Git)
3. **Netlify** (automáticamente versionado)

Puedes descargar versiones antiguas desde Netlify → Deploys

---

## 🎨 Personalizar después de Deploy

Para cambiar contenido sin tocar código:

### Cambiar contenido del entretenimiento
En `index.html`, busca:
```javascript
const ENTERTAINMENT_DATA = [
  { id: 1, title: 'Oppenheimer', ... }
]
```
Edita y haz push.

### Cambiar categorías de noticias
En `index.html`, busca:
```javascript
const CATEGORIES = [
  { id: 'TECH', color: '#a855f7', ... }
]
```

### Cambiar colores
Modifica los valores de `color` en CATEGORIES

---

## 🔐 Seguridad en Netlify

✅ **SSL/HTTPS** - Automático
✅ **DDoS Protection** - Incluido
✅ **Firewalls** - Disponibles (plan Pro)
✅ **Git Integration** - Solo tú haces push
✅ **Environment Variables** - Protegidas

---

## 📈 Próximos Pasos

### Inmediatos
1. Deploy en Netlify (Opción 1, 2 o 3)
2. Verifica que funcione
3. Comparte la URL

### Después
1. Agregar dominio personalizado
2. Configurar analytics
3. Agregar Netlify Forms si quieres feedback real

### Si quieres más features
- **Netlify Functions** - Backend ligero
- **Netlify Forms** - Procesar formularios
- **Netlify Redirects** - URLs amigables

---

## 🎯 Resumen Netlify vs Local

| Fase | Local | Netlify |
|------|-------|---------|
| Desarrollo | Tu computadora | Tu computadora |
| Test | http://localhost | http://localhost |
| Deploy | Git push | Git push (automático) |
| Publicado | En Netlify | En Netlify (en vivo) |
| Actualizaciones | Git push | Automático en < 30s |
| URL | astrak-xxxxx.netlify.app | Tu dominio o netlify.app |

---

## ✨ Lo que tienes listo

```
✅ index.html                (código completo)
✅ netlify.toml              (config Netlify)
✅ .gitignore                (control versiones)
✅ img/favicon.png           (tu favicon)
✅ img/logo.png              (tu logo)
✅ README.md                 (documentación)
✅ DEPLOYMENT.md             (esta guía)
✅ STRUCTURE.md              (estructura del proyecto)
```

**¡Listo para Netlify!**

---

## 🚀 Comando Rápido Final

```bash
# 1. En tu carpeta del proyecto
git init
git add .
git commit -m "ASTRAK v2 - Ready for Netlify"

# 2. Push a GitHub
git remote add origin https://github.com/tu-usuario/astrak.git
git branch -M main
git push -u origin main

# 3. En Netlify.com → New site from Git → Deploy
```

**Todo en < 5 minutos.**

---

**¡Felicidades! Tu ASTRAK está pronto para vivir en Netlify! 🎉**
