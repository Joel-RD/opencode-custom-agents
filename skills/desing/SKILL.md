---
name: frontend-design
description: >
  Creates distinctive, production-grade frontend interfaces with exceptional design quality
  and best practices. Use this skill whenever the user asks to build web components, pages,
  applications, dashboards, landing pages, UI elements, or any visual interface — even if
  they don't mention "design" explicitly. Also triggers when the user wants to improve,
  restyle, or evaluate an existing frontend. This skill prioritizes creative freedom, context
  gathering, accessibility, and code quality over templates or preset styles.
---

# Frontend Design Skill

Guides the creation of memorable, production-grade interfaces through intentional creativity,
user context, accessibility, and quality code — free from generic AI aesthetics.

---

## Phase 1: Gather Context

**NEVER start coding immediately.** Always, without exception, use the `ask_user_input` tool
to ask the user questions before writing a single line of code.
Combine questions into a maximum of 3 interactions.

### Topics to ask about:

**1. Technical stack**
- What framework or stack will you use? (plain HTML/CSS/JS, React, Vue, Next.js, etc.)
- Is there an existing styling system? (Tailwind, styled-components, CSS Modules, etc.)
- Is there an existing codebase to follow or extend?

**2. Purpose and audience**
- What is this interface for? (app, landing page, dashboard, component, etc.)
- Who will use it? (general public, professionals, internal team, etc.)
- What feeling should it convey? (trust, energy, calm, urgency, luxury, etc.)

**3. Aesthetic preferences**
- Are there brand constraints? (colors, fonts, logos, style guides)
- Are there visual references or examples you like?
- What is the single most important thing this interface must accomplish?

> If the user says "surprise me" or "you decide" — proceed with full creative freedom.
> Infer context from any code or screenshots they've already shared.

---

## Phase 2: Creative Direction

After gathering context, **define a unique aesthetic direction derived from the answers**
before writing any code. There are no defaults. Every design decision must be
justified by the context.

### How to derive the direction

Every element — color, typography, motion, composition — must answer directly to:

- **What is it for?** Purpose defines everything. A legal tool and a music app
  demand completely different visual languages.
- **Who uses it?** Age, culture, technical familiarity, and accessibility needs
  all inform the visual vocabulary.
- **What should the user feel?** Map the emotional intent to visual decisions:
  texture, weight, contrast, rhythm, space.
- **What would be unexpected but right?** Go beyond the obvious. The best direction
  often comes from combining two ideas that don't usually go together but make total sense
  for this context.

### No assumptions, no defaults

- There is no default color palette. The palette emerges from the concept.
- There is no default typography. It is chosen to serve the tone and audience.
- There is no default layout. Structure follows content and user flow.
- There is no default level of animation. Motion is only included if it earns its place.

### What to define before coding

State briefly (2–3 sentences max):
1. **Concept**: The core design idea — what is this design *saying*?
2. **Palette**: The colors chosen and why — what emotion or context do they serve?
3. **Typography**: The typefaces chosen and why — what character do they bring?
4. **Motion**: What moves, why, and how much — or why nothing moves.

---

## Phase 3: Frontend-Oriented Best Practices

### SOLID Principles Applied to Components

| Principle | Frontend Application |
|-----------|---------------------|
| **S** — Single Responsibility | Each component does one thing: a `<Button>` doesn't handle business logic |
| **O** — Open/Closed | Extend components via props/slots, not by modifying the base component |
| **L** — Liskov Substitution | A child component must be able to replace the parent without breaking the UI |
| **I** — Interface Segregation | Small, specific props; avoid components with 15+ props |
| **D** — Dependency Inversion | Components receive data and callbacks; they don't generate them internally |

### General Rules

- **DRY**: Extract duplicated logic or styles into hooks, utilities, or CSS variables
- **KISS**: Prefer simple composition over premature complex abstractions
- **YAGNI**: Don't create component variants until they are needed
- **Fail fast**: Validate props and input states early and explicitly
- **Pure functions**: Prefer components without side effects when possible

### Design Patterns Refocused for Frontend

#### Creational
| Pattern | Frontend Application |
|---------|---------------------|
| **Factory** | Function that returns different components by type: `createWidget('chart' \| 'table')` |
| **Builder** | Build complex UI configurations step by step (dynamic forms, themes) |
| **Singleton** | Global state store (Zustand, Pinia, Redux) — a single shared instance |

#### Structural
| Pattern | Frontend Application |
|---------|---------------------|
| **Adapter** | Transform API data before passing it to a UI component |
| **Decorator** | Higher-Order Components (HOC) or wrappers that add behavior (auth, logging) |
| **Facade** | Custom hook that encapsulates multiple API calls or complex logic |
| **Proxy** | Intercept API calls for caching, authentication, or centralized error handling |

#### Behavioral
| Pattern | Frontend Application |
|---------|---------------------|
| **Observer** | DOM events, store subscriptions, WebSockets, `EventEmitter` |
| **Strategy** | Swap rendering or validation algorithms at runtime |
| **Command** | Encapsulated UI actions for undo/redo, operation queues |
| **Repository** | Abstraction layer for API calls — separating fetch logic from component logic |

### Frontend-Specific Patterns

| Pattern | Description |
|---------|-------------|
| **Container / Presentational** | Separate components that fetch data from those that only render UI |
| **Compound Components** | Components that share implicit state (`<Select>` + `<Option>`) |
| **Render Props** | Pass a function as a prop to control what a component renders |
| **Custom Hooks** | Encapsulate reusable stateful logic (`useFetch`, `useForm`, `useDebounce`) |
| **Local vs Global State** | Ephemeral UI state → local; state shared across routes → global |
| **Lazy Loading** | Load components and routes only when needed (`React.lazy`, `defineAsyncComponent`) |
| **Error Boundaries** | Wrap UI sections to catch errors without breaking the entire application |

---

## Phase 4: Implementation Plan

**Always generate a plan before coding**, based on the gathered context.

- **Project structure**: What files will be created and what will each contain?
- **Technologies to use**: What libraries, frameworks, or tools will be used?
- **Dependencies**: What packages need to be installed?
- **Installation**: Install dependencies so the project works correctly
- **Verification**: Confirm correct installation of dependencies and tools
- **Workflow**: How will the different components connect?
- **Testing**: How will correct functionality be validated?

> For simple structure projects (single component, simple landing page),
> the plan can be brief — but it must always exist.

---

## Phase 5: Implementation

### Typography
- Load fonts from Google Fonts or similar — always include `@import` or `<link>` tags
- Define fallback font stacks
- Use `font-display: swap` for web performance
- Establish a clear typographic scale using CSS variables

### Color and Theme
- Define all colors as CSS custom properties (`--color-primary`, `--color-surface`, etc.)
- Ensure sufficient contrast (minimum 4.5:1 for body text, 3:1 for large text — WCAG AA)
- Design for both light and dark modes when appropriate, using `prefers-color-scheme`

### Motion and Animation
- Every animation must have a purpose: feedback, orientation, or delight
- Always include `@media (prefers-reduced-motion: reduce)` to disable or reduce animations
- Use CSS transitions for simple state changes; JS animations for orchestrated sequences
- Avoid infinite loops that serve no purpose

### Spatial Composition
- Break the grid deliberately and purposefully — not by accident
- Use whitespace as a design element, not just padding
- Consider diagonal flow, overlapping elements, or asymmetric balance where appropriate

### Responsive Design (Required)
- Always design mobile-first using `min-width` breakpoints
- Touch targets must be at least 44×44px on mobile
- Avoid fixed pixel widths for containers

### Code Quality
- Use semantic HTML elements (`<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, etc.)
- Use CSS variables for all repeated values (colors, spacing, radii, transitions)
- Keep component logic separate from presentation logic
- Avoid inline styles unless dynamically computed

---

## Phase 6: Accessibility (Non-Negotiable)

Accessibility is not optional. Apply these rules to every output:

### Structure
- Every page must have a logical heading hierarchy (`h1` → `h2` → `h3`)
- Landmark regions must be present (`<header>`, `<nav>`, `<main>`, `<footer>`)
- All images need descriptive `alt` text (or `alt=""` if purely decorative)

### Interactivity
- All interactive elements must be keyboard-navigable (Tab, Enter, Space, arrow keys)
- Visible focus indicators are required — never `outline: none` without a custom replacement
- Use `aria-label`, `aria-describedby`, `role` attributes where native semantics are insufficient
- Modals must trap focus when open and restore it on close

### Color
- Never convey information through color alone — always add a secondary signal (icon, text, pattern)

### Forms
- Every `<input>` must have an associated `<label>` (not just a placeholder)
- Error messages must be descriptive and programmatically associated with the field

---

## Phase 7: Quality Checklist

Before delivering any output, verify each point:

**Visual**
- [ ] Typography creates a clear hierarchy and is readable at all sizes
- [ ] Color contrast meets WCAG AA minimums
- [ ] The design is cohesive — no elements feel "out of place"
- [ ] Background or texture adds depth without overwhelming the content

**Code**
- [ ] All CSS values use variables — no magic numbers
- [ ] Fonts load correctly with proper fallbacks
- [ ] No broken layouts at mobile widths
- [ ] No unused CSS classes or commented-out dead code

**Components**
- [ ] Each component has a single, clear responsibility
- [ ] Dependencies are injected, not created inside the component
- [ ] Functions under ~20 lines with descriptive names (verb + noun)
- [ ] No props with more than 4–5 parameters (use objects if needed)
- [ ] No magic numbers — use named constants

**Accessibility**
- [ ] Heading hierarchy is logical
- [ ] All interactive elements are keyboard-accessible
- [ ] Focus indicators are visible
- [ ] `prefers-reduced-motion` is handled
- [ ] Images have alt text

**Performance**
- [ ] No heavy external dependencies loaded unnecessarily
- [ ] Animations use `transform` and `opacity` (GPU-composited) rather than layout properties
- [ ] Fonts use `font-display: swap`
- [ ] Lazy loading applied to heavy routes and components

---

## Framework-Specific Best Practices

### HTML / CSS / Vanilla JS
- Use CSS custom properties extensively
- Prefer CSS Grid and Flexbox over floats or absolute positioning
- Use `<template>` elements and JS for repeating dynamic content
- Validate HTML structure mentally (avoid "div soup")

### React
- Separate container components (logic) from presentational components (UI)
- Use CSS Modules or styled-components — avoid inline styles for static elements
- Memoize expensive renders with `useMemo`/`useCallback` when appropriate
- Accessible components: use `aria-*` props and native elements wherever possible

### Vue
- Use `<script setup>` and Composition API for reusable logic
- Separate stores (Pinia) from component logic
- Prefer named slots over complex props for UI composition

### Tailwind (when explicitly requested)
- Tailwind is a utility framework, not a design system — combine with custom CSS for truly unique results
- Extract repeated utility combos into `@apply` classes to keep HTML readable
- Extend the theme in `tailwind.config` rather than using arbitrary values everywhere

---

## Anti-Patterns to Avoid

| ❌ Don't | ✅ Do Instead |
|----------|--------------|
| Choose a familiar font because it's comfortable | Choose typography that serves the tone and audience |
| Use any color palette without reasoning | Derive the palette from the concept and emotion |
| `outline: none` without a replacement | Design a custom focus ring that fits the aesthetic |
| Animate because it looks good | Animate only what earns its place |
| Repeat the same layout pattern | Let content and user flow dictate the structure |
| Fixed pixel containers | Use fluid, responsive units |
| `<div>` for buttons/links | Use semantic `<button>` or `<a>` |
| Placeholders instead of labels | Always associate `<label>` with `<input>` |
| Start coding without understanding context | Always derive design decisions from Phase 1 |
| Components with 10+ props | Split into subcomponents or use composition |
| Business logic inside UI components | Extract to hooks, services, or stores |
| Data fetching inside presentational components | Use container/presentational pattern or hooks |

---

## Communicating Your Choices

When delivering the output, briefly explain:
1. **The concept** — what aesthetic direction was chosen and why
2. **Key decisions** — 2–3 notable design choices and their reasoning
3. **How to customize** — point the user to the CSS variables or props they'd most likely want to change

This is not a lengthy essay — keep it to 4–6 sentences. The goal is to make the user feel
informed and in control, not overwhelmed.

---

## Iteration Protocol

After delivering the output:
- Invite specific feedback: *"What would you like to adjust — layout, colors, typography, interactions?"*
- If the user asks for changes, apply them without rebuilding from scratch unless necessary
- If feedback is vague ("make it better"), ask one focused clarifying question before proceeding