---
name: login-split-branding
description: Crea y refactoriza pantallas de login con estilo visual distintivo tipo split layout (panel de marca + panel de acceso), manteniendo usabilidad y accesibilidad. Usar cuando el usuario pida rediseñar login, mejorar estilo visual, hacerlo menos genérico, modernizar formulario de acceso o aplicar branding institucional.
inclusion: manual
---

# Login Split Branding

## Objetivo

Transformar un login "genérico" en una experiencia visual con identidad propia, sin romper la logica de autenticacion.

## Cuando usar esta skill

- El usuario dice: "hazlo mas moderno", "se ve muy comun", "quiero otro estilo de login".
- El proyecto necesita apariencia institucional o de producto.
- Se quiere mantener backend/auth actual y cambiar solo UI/UX.

## Resultado esperado

- Layout tipo split:
  - Panel izquierdo: branding, mensaje de valor y elementos visuales.
  - Panel derecho: formulario limpio de acceso.
- Responsive:
  - Desktop: dos paneles.
  - Mobile: una sola columna, simplificando el panel de branding.
- Formularios legibles:
  - Labels fijos y claros.
  - Espaciado consistente.
  - CTA principal visible.

## Flujo recomendado

1. Identificar archivos de login (`index.html`, `login.html`, `styles.css` o estilos inline).
2. Conservar ids y hooks de JS (`loginForm`, `username`, `password`, contenedor de errores).
3. Reestructurar HTML a `login-shell` con `login-brand-panel` y `login-box`.
4. Agregar estilos de:
   - grid split,
   - glassmorphism suave,
   - tipografia jerarquica,
   - tarjetas de metrica/branding opcionales.
5. Definir media query para colapsar a una columna en mobile.
6. Verificar que el submit y mensajes de error sigan funcionando.

## Plantilla de clases CSS sugeridas

- Contenedor general:
  - `.login-container`
  - `.login-shell`
- Branding:
  - `.login-brand-panel`
  - `.brand-badge`
  - `.brand-title`
  - `.brand-subtitle`
  - `.brand-stats`
  - `.brand-stat`
- Formulario:
  - `.login-box`
  - `.login-logo`
  - `.login-skill`
  - `.login-field`

## Reglas de calidad

- No cambiar nombres/ids consumidos por JS.
- No mover rutas API ni scripts de auth.
- Mantener contraste y legibilidad en claro/oscuro.
- No saturar con animaciones largas; usar transiciones cortas.
- Priorizar performance (sin librerias externas para un login simple).

## Checklist de validacion final

- [ ] El formulario inicia sesion correctamente.
- [ ] El error de login se muestra en la posicion correcta.
- [ ] En desktop se ve split layout.
- [ ] En mobile no hay solapamientos ni overflow horizontal.
- [ ] Boton principal y campos son faciles de usar.

## Nota de implementacion

Si el usuario pide "otra variante", reutilizar la misma estructura y cambiar solo:

- paleta de color,
- densidad visual (mas sobrio o mas expresivo),
- estilo del panel de marca (corporativo, academico o dark-tech).
