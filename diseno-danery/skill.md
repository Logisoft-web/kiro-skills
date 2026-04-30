---
name: diseno-danery
description: Mega-skill de diseño frontend que combina lo mejor de 22 skills de diseño en una sola. Crea interfaces distintivas, production-grade con tipografía excepcional, color estratégico, layouts intencionales, animaciones sutiles y refinamiento meticuloso. Usa esta skill para cualquier trabajo de diseño visual: login, dashboards, landing pages, componentes, sistemas de diseño completos. Evita estética genérica de AI y produce diseños memorables con identidad propia.
version: 1.0.0
user-invocable: true
argument-hint: "[craft|audit|polish|teach]"
license: MIT - Basado en las mejores prácticas de diseño UI/UX
---

# 🎨 Diseño Danery - Mega Skill de Diseño Frontend

**La skill definitiva de diseño visual que combina lo mejor de 22 skills especializadas.**

Esta skill es tu compañero experto para crear interfaces web excepcionales que:
- ✨ Tienen personalidad e identidad propia
- 🎯 Comunican jerarquía visual clara
- 🚀 Son production-ready desde el primer momento
- ♿ Cumplen estándares de accesibilidad
- 📱 Funcionan perfectamente en todos los dispositivos
- 🎭 Evitan la estética genérica de AI

---

## 🎯 Cuándo Usar Esta Skill

**USA esta skill cuando necesites:**
- Diseñar pantallas de login con branding distintivo
- Crear landing pages memorables
- Construir dashboards y aplicaciones web
- Diseñar sistemas de componentes UI
- Refinar interfaces existentes
- Aplicar identidad visual a proyectos
- Mejorar tipografía, color, spacing o layout
- Hacer auditoría de diseño completa

**NO uses esta skill para:**
- Backend o APIs (usa skills de backend)
- Lógica de negocio o base de datos
- Testing o deployment (usa skills específicas)

---

## 🧠 Filosofía de Diseño

### El Problema del "AI Slop"

La mayoría de interfaces generadas por AI se ven iguales:
- Fuentes genéricas (Inter, Roboto, Arial)
- Paletas predecibles (gradientes púrpura-azul)
- Layouts monótonos (grids de cards idénticas)
- Glassmorphism sin propósito
- Números grandes sin significado real

**Diseño Danery rechaza esto completamente.**

### Los 3 Pilares del Diseño Excepcional

```
┌─────────────────────────────────────────────────────────────┐
│  1. INTENCIONALIDAD                                         │
│     Cada decisión tiene un propósito claro.                 │
│     No hay elementos decorativos sin razón.                 │
│                                                             │
│  2. IDENTIDAD                                               │
│     El diseño refleja la marca y audiencia.                 │
│     Es memorable y reconocible.                             │
│                                                             │
│  3. REFINAMIENTO                                            │
│     Atención meticulosa a cada detalle.                     │
│     Spacing, alineación, estados, transiciones.             │
└─────────────────────────────────────────────────────────────┘
```

---

## 🎨 Principios de Diseño Visual

### 1. Tipografía Excepcional

**Selección de Fuentes:**
- ❌ NUNCA uses: Inter, Roboto, Arial, Open Sans, system fonts
- ❌ NUNCA uses: Fraunces, Newsreader, Lora, Crimson, Playfair, Cormorant, Syne, Space Grotesk, DM Sans, Outfit, Plus Jakarta Sans
- ✅ Busca fuentes con personalidad: Google Fonts, Pangram Pangram, Future Fonts, Adobe Fonts
- ✅ Combina display font distintivo + body font refinado
- ✅ Máximo 2-3 familias tipográficas

**Jerarquía Tipográfica:**
```css
/* Escala modular con ratio 1.25 - 1.5 */
--text-xs: 0.75rem;    /* 12px - captions */
--text-sm: 0.875rem;   /* 14px - secondary */
--text-base: 1rem;     /* 16px - body */
--text-lg: 1.25rem;    /* 20px - subheadings */
--text-xl: 1.5rem;     /* 24px - headings */
--text-2xl: 2rem;      /* 32px - titles */
--text-3xl: 3rem;      /* 48px - display */
```

**Reglas de Oro:**
- Line-height: 1.5-1.7 para body, 1.1-1.2 para headings
- Max-width: 65-75ch para texto largo
- Mínimo 16px para body text
- Usar `rem` en lugar de `px`
- Fluid sizing con `clamp()` para headings en marketing
- Fixed sizing para UIs de aplicaciones

### 2. Color Estratégico (OKLCH)

**Sistema de Color Moderno:**
```css
/* Usar OKLCH - perceptualmente uniforme */
--primary: oklch(60% 0.15 250);      /* Azul vibrante */
--primary-light: oklch(85% 0.08 250); /* Tint claro */
--primary-dark: oklch(40% 0.18 250);  /* Shade oscuro */

/* Neutrales con tinte de marca */
--neutral-50: oklch(97% 0.01 250);   /* Casi blanco con tinte */
--neutral-900: oklch(20% 0.01 250);  /* Casi negro con tinte */
```

**Regla 60-30-10:**
- 60% → Color dominante / neutrales
- 30% → Color secundario
- 10% → Color de acento (high contrast)

**Colores Semánticos:**
- Success: Verde (emerald, forest, mint)
- Error: Rojo/Rosa (rose, crimson, coral)
- Warning: Naranja/Ámbar
- Info: Azul (sky, ocean, indigo)

**PROHIBIDO:**
- ❌ Texto gris sobre fondos de color (usar shade del fondo)
- ❌ Negro puro (#000) o blanco puro (#fff)
- ❌ Gradientes en texto (background-clip: text)
- ❌ Paleta AI: cyan-on-dark, purple-blue gradients
- ❌ Glassmorphism decorativo sin propósito

### 3. Layout & Spacing Intencional

**Sistema de Spacing (4pt base):**
```css
--space-xs: 0.25rem;   /* 4px */
--space-sm: 0.5rem;    /* 8px */
--space-md: 0.75rem;   /* 12px */
--space-lg: 1rem;      /* 16px */
--space-xl: 1.5rem;    /* 24px */
--space-2xl: 2rem;     /* 32px */
--space-3xl: 3rem;     /* 48px */
--space-4xl: 4rem;     /* 64px */
--space-5xl: 6rem;     /* 96px */
```

**Principios de Layout:**
- Usar `gap` en lugar de margins para siblings
- Spacing variado crea ritmo visual
- Agrupación tight (8-12px) para elementos relacionados
- Separación generosa (48-96px) entre secciones
- Asimetría intencional > todo centrado

**Grid vs Flexbox:**
- Flexbox → Layouts 1D (rows, navbars, card contents)
- Grid → Layouts 2D (page structure, dashboards)
- `repeat(auto-fit, minmax(280px, 1fr))` → responsive sin breakpoints

**PROHIBIDO:**
- ❌ Cards dentro de cards (usar spacing y dividers)
- ❌ Grids idénticas de cards en todas partes
- ❌ Hero metric layout como template
- ❌ Border-left > 1px como accent stripe
- ❌ Todo centrado sin razón
- ❌ Spacing arbitrario fuera del sistema

### 4. Animaciones & Micro-interacciones

**Timing & Easing:**
```css
/* Transiciones naturales */
--duration-fast: 150ms;
--duration-base: 250ms;
--duration-slow: 350ms;

/* Easing exponencial - natural deceleration */
--ease-out: cubic-bezier(0.16, 1, 0.3, 1);  /* ease-out-expo */
--ease-in-out: cubic-bezier(0.87, 0, 0.13, 1); /* ease-in-out-expo */
```

**Reglas de Animación:**
- Solo animar `transform` y `opacity` (performance)
- Usar `will-change` con cuidado
- Respetar `prefers-reduced-motion`
- ❌ NUNCA bounce o elastic easing (se ven anticuados)
- Stagger reveals con `animation-delay` para page loads

### 5. Estados de Interacción

**Cada elemento interactivo necesita:**
```css
/* Estados completos */
.button {
  /* Default */
  background: var(--primary);
  transition: all var(--duration-base) var(--ease-out);
}

.button:hover {
  /* Hover - feedback sutil */
  transform: translateY(-2px);
  box-shadow: var(--shadow-lg);
}

.button:focus-visible {
  /* Focus - keyboard navigation */
  outline: 2px solid var(--primary);
  outline-offset: 2px;
}

.button:active {
  /* Active - click feedback */
  transform: translateY(0);
}

.button:disabled {
  /* Disabled - claramente no interactivo */
  opacity: 0.5;
  cursor: not-allowed;
}
```

### 6. Responsive Design

**Breakpoints Estándar:**
```css
/* Mobile first */
/* Default: < 768px */

@media (min-width: 768px) {
  /* Tablet */
}

@media (min-width: 1024px) {
  /* Desktop */
}

@media (min-width: 1440px) {
  /* Extra Large */
}
```

**Reglas Responsive:**
- Mobile first (default sin prefijo)
- Touch targets mínimo 44x44px
- Texto mínimo 14px en mobile
- Sin scroll horizontal
- Container queries para componentes

---

## 🎭 Modos de Operación

### Modo 1: CRAFT (Diseño Completo)

**Uso:** `/diseno-danery craft [descripción del feature]`

**Proceso:**
1. **Discovery Interview** - Entender contexto, audiencia, objetivos
2. **Design Brief** - Documento estructurado con decisiones
3. **Implementation** - Código production-ready
4. **Polish** - Refinamiento final

**Ideal para:** Proyectos nuevos, features complejos, cuando necesitas pensar antes de codear

### Modo 2: AUDIT (Evaluación de Diseño)

**Uso:** `/diseno-danery audit [target]`

**Proceso:**
1. **AI Slop Detection** - ¿Se ve genérico?
2. **Heuristics Scoring** - Nielsen's 10 heuristics (0-40 puntos)
3. **Cognitive Load** - ¿Es fácil de usar?
4. **Persona Testing** - ¿Funciona para usuarios reales?
5. **Action Plan** - Recomendaciones priorizadas

**Ideal para:** Revisar diseños existentes, pre-launch review, mejora continua

### Modo 3: POLISH (Refinamiento Final)

**Uso:** `/diseno-danery polish [target]`

**Proceso:**
1. **Visual Alignment** - Pixel-perfect
2. **Spacing Consistency** - Sistema aplicado
3. **Typography Refinement** - Jerarquía clara
4. **Interaction States** - Todos los estados
5. **Edge Cases** - Loading, error, empty states
6. **Performance** - Sin jank, CLS, optimizado

**Ideal para:** Antes de lanzar, últimos detalles, de bueno a excelente

### Modo 4: TEACH (Contexto de Diseño)

**Uso:** `/diseno-danery teach`

**Proceso:**
1. **Explorar Codebase** - Entender proyecto actual
2. **Preguntas UX** - Audiencia, marca, objetivos
3. **Design Context** - Documento `.impeccable.md`
4. **Design Principles** - Guías para futuro trabajo

**Ideal para:** Primera vez en proyecto, establecer dirección, onboarding

---

## 🚀 Flujo de Trabajo Recomendado

### Para Login / Pantallas de Autenticación

```bash
# 1. Establecer contexto (primera vez)
/diseno-danery teach

# 2. Diseñar login completo
/diseno-danery craft "pantalla de login con split layout, 
panel izquierdo con branding institucional, 
panel derecho con formulario limpio"

# 3. Refinar detalles
/diseno-danery polish login.html

# 4. Auditar antes de lanzar
/diseno-danery audit login.html
```

### Para Landing Pages

```bash
# 1. Contexto + diseño
/diseno-danery craft "landing page para [producto], 
audiencia [descripción], tono [personalidad]"

# 2. Auditoría intermedia
/diseno-danery audit index.html

# 3. Polish final
/diseno-danery polish index.html
```

### Para Dashboards / Apps

```bash
# 1. Establecer sistema de diseño
/diseno-danery teach

# 2. Crear componentes base
/diseno-danery craft "sistema de componentes: 
buttons, inputs, cards, navigation"

# 3. Implementar features
/diseno-danery craft "dashboard con métricas, 
tabla de datos, filtros"

# 4. Consistencia final
/diseno-danery audit src/
/diseno-danery polish src/
```

---

## ✅ Checklist de Calidad

### Tipografía
- [ ] Fuentes distintivas (no Inter/Roboto/Arial)
- [ ] Escala modular consistente (ratio 1.25+)
- [ ] Line-height apropiado (1.5-1.7 body, 1.1-1.2 headings)
- [ ] Max-width 65-75ch para texto largo
- [ ] Mínimo 16px para body text

### Color
- [ ] Paleta OKLCH con tinte en neutrales
- [ ] Regla 60-30-10 aplicada
- [ ] Contraste WCAG AA mínimo (4.5:1 texto, 3:1 UI)
- [ ] Sin texto gris sobre fondos de color
- [ ] Sin negro/blanco puros

### Layout
- [ ] Sistema de spacing 4pt aplicado consistentemente
- [ ] Spacing variado (tight grouping, generous separation)
- [ ] Sin cards dentro de cards
- [ ] Responsive en mobile, tablet, desktop
- [ ] Touch targets 44x44px mínimo

### Interacción
- [ ] Todos los estados: default, hover, focus, active, disabled
- [ ] Transiciones suaves (150-350ms)
- [ ] Easing exponencial (no bounce/elastic)
- [ ] Respeta prefers-reduced-motion
- [ ] Focus indicators visibles

### Contenido
- [ ] Copy consistente y claro
- [ ] Estados vacíos útiles
- [ ] Mensajes de error claros
- [ ] Loading states visibles
- [ ] Sin console.log en producción

### Accesibilidad
- [ ] Contraste WCAG AA
- [ ] Navegación por teclado funcional
- [ ] Focus indicators nunca removidos
- [ ] Alt text en imágenes
- [ ] Semántica HTML correcta

---

## 🎯 Patrones de Diseño Específicos

### Login Split Branding

```html
<div class="login-shell">
  <!-- Panel de Marca -->
  <div class="login-brand-panel">
    <div class="brand-badge">
      <img src="logo.svg" alt="Logo">
    </div>
    <h1 class="brand-title">Bienvenido</h1>
    <p class="brand-subtitle">Mensaje de valor institucional</p>
    <div class="brand-stats">
      <!-- Métricas reales, no decorativas -->
    </div>
  </div>

  <!-- Panel de Formulario -->
  <div class="login-box">
    <h2 class="login-title">Iniciar Sesión</h2>
    <form id="loginForm">
      <div class="login-field">
        <label for="username">Usuario</label>
        <input type="text" id="username" required>
      </div>
      <div class="login-field">
        <label for="password">Contraseña</label>
        <input type="password" id="password" required>
      </div>
      <button type="submit" class="btn-primary">Ingresar</button>
    </form>
  </div>
</div>
```

```css
.login-shell {
  display: grid;
  grid-template-columns: 1fr 1fr;
  min-height: 100vh;
}

.login-brand-panel {
  background: linear-gradient(135deg, 
    oklch(60% 0.15 250), 
    oklch(40% 0.18 270));
  color: white;
  padding: var(--space-4xl);
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.login-box {
  padding: var(--space-4xl);
  display: flex;
  flex-direction: column;
  justify-content: center;
  max-width: 400px;
  margin: 0 auto;
}

/* Responsive */
@media (max-width: 767px) {
  .login-shell {
    grid-template-columns: 1fr;
  }
  
  .login-brand-panel {
    padding: var(--space-2xl);
    min-height: 30vh;
  }
}
```

### Dashboard Metrics (No Hero Layout)

```html
<!-- ❌ MAL: Hero metric decorativo -->
<div class="metric-card">
  <div class="big-number">1,234</div>
  <div class="label">Users</div>
</div>

<!-- ✅ BIEN: Datos reales con contexto -->
<div class="metric-card">
  <div class="metric-header">
    <span class="metric-label">Usuarios Activos</span>
    <span class="metric-change positive">+12%</span>
  </div>
  <div class="metric-value">1,234</div>
  <div class="metric-context">vs. 1,102 mes anterior</div>
  <div class="metric-sparkline">
    <!-- Gráfico real, no decorativo -->
  </div>
</div>
```

---

## 🚫 Anti-Patrones Absolutos

### PROHIBIDO - Nunca Usar

```css
/* ❌ Border-left accent stripe */
.card {
  border-left: 4px solid var(--primary); /* NUNCA */
}

/* ❌ Gradient text */
.title {
  background: linear-gradient(...);
  -webkit-background-clip: text; /* NUNCA */
}

/* ❌ Glassmorphism decorativo */
.card {
  backdrop-filter: blur(10px); /* Solo si tiene propósito */
}

/* ❌ Fuentes genéricas */
body {
  font-family: Inter, sans-serif; /* NUNCA */
}

/* ❌ Spacing arbitrario */
.element {
  margin: 13px; /* Usar sistema de spacing */
}
```

---

## 📚 Referencias Rápidas

### Fuentes Recomendadas (Alternativas)

**Serif Display:**
- Fraunces → Crimson Pro, Lora, Newsreader
- Playfair → Cormorant, Libre Baskerville

**Sans-Serif:**
- Inter → Public Sans, Manrope, Satoshi
- Roboto → IBM Plex Sans, Work Sans

**Monospace:**
- Fira Code → JetBrains Mono, Cascadia Code

**Display/Decorative:**
- Explorar: Pangram Pangram, Future Fonts, ABC Dinamo

### Paletas de Color Inspiración

**Corporativo Confiable:**
```css
--primary: oklch(50% 0.15 250);    /* Azul profesional */
--secondary: oklch(45% 0.12 200);  /* Azul-verde */
--accent: oklch(65% 0.18 30);      /* Naranja cálido */
```

**Creativo Vibrante:**
```css
--primary: oklch(60% 0.20 330);    /* Magenta */
--secondary: oklch(70% 0.18 120);  /* Verde lima */
--accent: oklch(75% 0.15 60);      /* Amarillo */
```

**Elegante Refinado:**
```css
--primary: oklch(30% 0.08 280);    /* Azul oscuro */
--secondary: oklch(70% 0.05 40);   /* Beige dorado */
--accent: oklch(50% 0.12 20);      /* Terracota */
```

---

## 🎓 Recursos Adicionales

### Herramientas Recomendadas

- **Color:** [OKLCH Color Picker](https://oklch.com)
- **Tipografía:** [Type Scale](https://typescale.com)
- **Spacing:** [Spacing Calculator](https://spacing.app)
- **Contraste:** [Contrast Checker](https://webaim.org/resources/contrastchecker/)
- **Fuentes:** [Google Fonts](https://fonts.google.com), [Fontshare](https://fontshare.com)

### Inspiración de Diseño

- [Dribbble](https://dribbble.com) - Exploración visual
- [Awwwards](https://awwwards.com) - Sitios premiados
- [Land-book](https://land-book.com) - Landing pages
- [Mobbin](https://mobbin.com) - Patrones mobile

---

## 💡 Consejos Finales

1. **Piensa antes de codear** - Usa `craft` o `teach` para establecer dirección
2. **Sé distintivo** - Rechaza lo genérico, abraza la personalidad
3. **Suda los detalles** - El refinamiento separa lo bueno de lo excepcional
4. **Prueba en real** - Dispositivos reales, usuarios reales
5. **Itera** - Audita, mejora, pule, repite

---

**Diseño Danery** - Donde la excelencia visual se encuentra con la implementación impecable.

*Versión 1.0.0 - Abril 2026*
