# Sistema de Contexto Compartido

En lugar de briefs rígidos, usa el contexto compartido para tomar decisiones informadas.

---

## Qué es el Contexto Compartido

Es un estado vivo que se construye y actualiza durante la sesión:

- **Stack tecnológico** - Lenguajes, frameworks, libs
- **Patrones usados** - Arquitectura, convenciones
- **Decisiones tomadas** - Por qué se eligió X o Y
- **Estado del proyecto** - Fase actual, qué falta
- **Preferencias** - Estilo del usuario, patrones favoritos

---

## Cómo Usar el Contexto

### Antes de Actuar

1. **Lee el contexto disponible** - ¿Qué sé del proyecto?
2. **Analiza el código existente** - Patrones, estructura
3. **Infiere lo que falta** - ¿Qué necesito saber?

### Durante la Ejecución

1. **Actualiza el contexto** - Cuando tomes decisiones importantes
2. **Registra cambios** - Nueva arquitectura, libs añadidas
3. **Comparte conocimiento** - Para que otros agentes puedan beneficiarse

### Formato Sugerido

Guarda el contexto en memoria o en un archivo `.context.md`:

```markdown
# Contexto del Proyecto

## Stack
- Runtime: Node.js
- Framework: Express
- DB: PostgreSQL con Prisma

## Patrones
- Repository pattern
- DTOs con Zod
- Middleware de autenticación

## Estado
- API REST básica completa
- Falta: tests, documentación

## Decisiones
- JWT para auth
- Error handling centralizado

## Notas
- Usuario prefiere código funcional sobre ideal
- Evitar over-engineering
```

---

## Gestión Flexible

### Si falta información

- **Deduce** lo más razonable según el contexto
- **Pregunta** solo si es crítico y no hay forma de inferir
- **Asume** patrones estándar si no hay prefs claras

### Si el contexto evoluciona

- Actualiza cuando tomes decisiones significativas
- Mantén el contexto limpio y relevante
- No guardes información obsoleta

---

## Beneficios

- **Menos rigidez** - No necesitas specs completos
- **Más dinamismo** - El agente adapta según contexto
- **Mejor colaboración** - Agentes comparten conocimiento
- **Decisiones informadas** - Siempre hay contexto para guiar

---

## Nota Importante

El contexto es una **guía**, no una restricción. Usa tu criterio para interpretar y actualizar.
