# Infinite Ventures — SPEC-003

**Specification ID:** SPEC-003
**Title:** Preparar la estructura física inicial de la aplicación
**Project Phase:** Fase 01 — Foundations and Architecture
**Status:** Approved
**Version:** 1.0

---

# 1. Objective

Establecer la estructura física inicial del repositorio de Infinite Ventures, siguiendo el stack tecnológico y las decisiones arquitectónicas previamente aprobadas.

La especificación define una base técnica mínima, modular y ejecutable que permita iniciar el desarrollo incremental de la aplicación sin implementar todavía funcionalidad del juego.

---

# 2. Business and Technical Value

## Business Value

- Proporcionar una base técnica sobre la cual desarrollar progresivamente Infinite Ventures.
- Evitar estructuras prematuras que dificulten la evolución del proyecto.
- Facilitar la implementación independiente de los sistemas mediante futuras SPEC.
- Mantener coherencia entre la arquitectura documentada y la estructura física del repositorio.

## Technical Value

- Configuración funcional de Vite para desarrollo y construcción.
- Aplicación web estática basada en HTML5.
- JavaScript organizado mediante ES Modules.
- CSS modularizado por responsabilidades.
- Dependencias externas limitadas a las herramientas de desarrollo autorizadas.
- Base reproducible mediante `package-lock.json`.

---

# 3. Context and References

| Reference | Purpose |
|---|---|
| Issue #01 | Documentación técnica inicial del proyecto |
| Issue #02 | Inicialización del repositorio y control de versiones |
| Issue #05 | Definición del stack tecnológico y arquitectura modular |
| SPEC-001 | Especificación aprobada del stack tecnológico y arquitectura modular |
| SPEC-002 | Configuración de OpenCode y directrices del agente |
| Issue #06 | Trabajo actual: preparación de la estructura física inicial |
| `docs/ARCHITECTURE.md` | Responsabilidades y límites de los sistemas lógicos |
| `docs/PROJECT_CONTEXT.md` | Restricciones, tecnologías y reglas de ejecución del proyecto |

La GitHub Wiki continúa siendo la fuente de verdad para los requisitos de diseño del juego.

Esta SPEC no redefine requisitos del producto ni modifica decisiones arquitectónicas aprobadas.

---

# 4. Dependencies

| Dependency | Status | Relevance |
|---|---|---|
| Issue #01 — Documentación inicial | Completed | Proporciona el contexto y las plantillas del proyecto |
| Issue #02 — Inicialización del repositorio | Completed | Proporciona el repositorio y control de versiones |
| Issue #05 — Stack y arquitectura modular | Completed | Define las decisiones técnicas que debe respetar esta estructura |

No existen dependencias funcionales respecto a sistemas del juego.

---

# 5. Scope

## 5.1. Included

### 5.1.1. Configuración del proyecto

Crear `package.json` con:

- Metadatos básicos del proyecto.
- Configuración compatible con ES Modules cuando corresponda.
- Vite como única dependencia externa autorizada.
- Vite declarado exclusivamente en `devDependencies`.
- Scripts npm esenciales.

Scripts requeridos:

| Script | Behavior |
|---|---|
| `npm run dev` | Iniciar el servidor de desarrollo de Vite |
| `npm run build` | Generar la construcción de producción |

La versión de Vite debe ser compatible con la versión de Node.js disponible en el entorno de implementación.

No se requiere un archivo `vite.config.js`. Se utilizará la configuración predeterminada de Vite mientras sea suficiente para cumplir esta SPEC.

### 5.1.2. Punto de entrada HTML5

Crear `index.html` como punto de entrada de la aplicación.

Debe:

- Utilizar HTML5.
- Definir los metadatos básicos del documento.
- Incluir un título identificativo de Infinite Ventures.
- Cargar `src/index.js` mediante un elemento `script` de tipo `module`.
- Permitir que Vite procese los recursos importados por el punto de entrada.

No debe introducir frameworks ni dependencias externas de ejecución.

### 5.1.3. Estructura JavaScript

Crear:

`src/index.js`

Responsabilidad:

- Ser el punto de entrada JavaScript de la aplicación.
- Importar únicamente `src/main.css`.
- No importar módulos de sistemas del juego.
- No implementar lógica de negocio, inicialización de sistemas ni funcionalidades futuras.

La importación CSS debe utilizar una ruta relativa válida:

`import './main.css';`

### 5.1.4. Estructura CSS

Crear:

`src/main.css`

Será el punto de entrada CSS y deberá importar los seis archivos siguientes, en el orden indicado:

| File | Responsibility |
|---|---|
| `src/styles/base.css` | Estilos base y normalización |
| `src/styles/tokens.css` | Variables CSS y tokens visuales |
| `src/styles/layout.css` | Organización general del layout |
| `src/styles/components.css` | Estilos de componentes |
| `src/styles/sections.css` | Estilos de secciones |
| `src/styles/utilities.css` | Utilidades CSS comunes |

`tokens.css` es obligatorio porque establece la base para las futuras decisiones visuales.

Los archivos CSS podrán contener únicamente las reglas o declaraciones mínimas justificadas por la responsabilidad de cada archivo. No se incorporarán estilos de interfaz definitiva ni contenido visual ficticio. No se crearán reglas sin una necesidad técnica concreta.

### 5.1.5. Control de versiones

Crear `.gitignore` para excluir como mínimo:

- `node_modules/`
- `dist/`
- `.vite/`

Crear `package-lock.json` mediante npm para registrar las dependencias instaladas y permitir reproducir el entorno.

El archivo debe generarse automáticamente. No debe editarse manualmente.

## 5.2. Excluded

Esta SPEC no autoriza:

- Implementar funcionalidad de ningún sistema del juego.
- Desarrollar economía, negocios, producción, managers o upgrades.
- Implementar hitos, expansión, prestigio o Corporate Legacy.
- Implementar persistencia funcional u offline progress.
- Desarrollar la interfaz visual definitiva.
- Crear gráficos, mapas, recursos visuales o contenido de negocios.
- Crear sistemas de testing automatizado.
- Configurar CI/CD o despliegue.
- Incorporar frameworks frontend.
- Incorporar dependencias externas adicionales.
- Crear archivos funcionales vacíos sin justificación.
- Crear directorios reservados para sistemas futuros.
- Crear `src/assets/` o `public/` sin una necesidad concreta previamente justificada.
- Crear un archivo `vite.config.js` si la configuración predeterminada es suficiente.
- Modificar documentación, Issues o GitHub Projects sin autorización específica.

La estructura física será incremental. Los módulos lógicos se incorporarán mediante sus respectivas SPEC aprobadas.

---

# 6. Requirements

## 6.1. Functional Requirements

**FR-01 — Desarrollo local**

El proyecto debe permitir iniciar un servidor de desarrollo mediante `npm run dev`.

**FR-02 — Construcción de producción**

El proyecto debe permitir generar una construcción de producción mediante `npm run build`, destinada a ejecutarse como aplicación web estática en navegadores compatibles.

**FR-03 — Punto de entrada**

La aplicación debe contar con un punto de entrada HTML5 que cargue correctamente el módulo JavaScript principal.

**FR-04 — Estilos**

El punto de entrada JavaScript debe cargar el punto de entrada CSS, que a su vez debe incorporar las seis capas CSS autorizadas.

## 6.2. Technical Requirements

**TR-01 — Tecnologías**

La estructura debe utilizar HTML5, CSS y JavaScript nativo mediante ES Modules, con Vite como herramienta de desarrollo y construcción.

**TR-02 — Dependencias**

Vite será la única dependencia externa autorizada en `devDependencies`. No se incorporarán dependencias de ejecución.

**TR-03 — Modularidad CSS**

Los estilos deben permanecer separados según las responsabilidades definidas en la sección 5.1.4.

**TR-04 — Modularidad JavaScript**

`src/index.js` será el único punto de entrada JavaScript inicial y únicamente importará `src/main.css`.

**TR-05 — Estructura incremental**

No se crearán directorios ni archivos de sistemas lógicos futuros sin una SPEC correspondiente aprobada.

**TR-06 — Configuración predeterminada**

Se utilizará la configuración predeterminada de Vite siempre que satisfaga los requisitos de esta especificación.

**TR-07 — Restricciones del proyecto**

Se respetarán las decisiones documentadas en `docs/PROJECT_CONTEXT.md` y `docs/ARCHITECTURE.md`.

---

# 7. Acceptance Criteria

| ID | Acceptance Criteria |
|---|---|
| AC-01 | Se crean únicamente los archivos y directorios autorizados en la sección 8, sin crear directorios para sistemas futuros ni modificar la estructura existente fuera del alcance aprobado. |
| AC-02 | La versión de Vite seleccionada es compatible con Node.js disponible en el entorno y permite ejecutar sus comandos CLI. |
| AC-03 | `package.json` contiene los metadatos necesarios y declara Vite como única dependencia externa en `devDependencies`, sin dependencias externas de ejecución. |
| AC-04 | Los scripts `npm run dev` y `npm run build` están definidos y se ejecutan correctamente. |
| AC-05 | `index.html` utiliza HTML5 e incluye la carga de `src/index.js` mediante `script type="module"`. |
| AC-06 | `src/index.js` importa únicamente `src/main.css`, sin importar módulos de sistemas del juego. |
| AC-07 | Existen los seis archivos CSS autorizados y `src/main.css` los importa en el orden establecido en la sección 8.3. |
| AC-08 | `package-lock.json` ha sido generado mediante npm y es consistente con `package.json`. |
| AC-09 | El servidor de desarrollo inicia correctamente y la aplicación puede cargarse en el navegador sin errores de carga atribuibles a esta estructura. |
| AC-10 | `npm run build` finaliza correctamente y genera `dist/` con la aplicación web estática de producción. |
| AC-11 | `.gitignore` excluye correctamente `node_modules/`, `dist/` y `.vite/`. |

Los criterios se verifican de forma independiente según su responsabilidad. La ejecución de scripts, la carga en navegador y la construcción de producción no se consideran equivalentes entre sí.

---

# 8. Authorized Files

Esta sección establece la lista cerrada de archivos cuya creación queda autorizada por esta SPEC.

No se autoriza modificar, eliminar, reemplazar ni renombrar archivos existentes.

## 8.1. Configuration Files

| File | Operation | Purpose |
|---|---|---|
| `package.json` | Create | Metadatos, dependencia Vite y scripts npm |
| `package-lock.json` | Create | Registro reproducible de dependencias |
| `.gitignore` | Create | Exclusión de dependencias instaladas y artefactos generados |

`package-lock.json` será generado automáticamente por npm.

## 8.2. HTML and JavaScript Entry Points

| File | Operation | Purpose |
|---|---|---|
| `index.html` | Create | Punto de entrada HTML5 |
| `src/index.js` | Create | Punto de entrada JavaScript |
| `src/main.css` | Create | Punto de entrada CSS |

## 8.3. CSS Source Files

| File | Operation | Purpose |
|---|---|---|
| `src/styles/base.css` | Create | Estilos base y normalización |
| `src/styles/tokens.css` | Create | Variables y tokens visuales |
| `src/styles/layout.css` | Create | Organización general del layout |
| `src/styles/components.css` | Create | Estilos de componentes |
| `src/styles/sections.css` | Create | Estilos de secciones |
| `src/styles/utilities.css` | Create | Utilidades CSS |

### CSS import order

El archivo `src/main.css` debe contener las siguientes importaciones en el orden indicado:

```css
@import './styles/base.css';
@import './styles/tokens.css';
@import './styles/layout.css';
@import './styles/components.css';
@import './styles/sections.css';
@import './styles/utilities.css';
```

El orden es obligatorio.

## 8.4. Directory Structure

La estructura física autorizada será:

```text
infinite-venture/
├── .gitignore
├── index.html
├── package.json
├── package-lock.json
└── src/
    ├── index.js
    ├── main.css
    └── styles/
        ├── base.css
        ├── tokens.css
        ├── layout.css
        ├── components.css
        ├── sections.css
        └── utilities.css
```

No se requiere crear directorios adicionales.

No se crearán directorios para Core, Game State, Economy, Persistence, Managers, Upgrades, Expansion, Prestige u otros sistemas futuros.

---

# 9. Implementation Constraints

1. Respetar las decisiones aprobadas en `docs/ARCHITECTURE.md` y `docs/PROJECT_CONTEXT.md`.
2. No implementar funcionalidad del juego.
3. No incorporar frameworks frontend.
4. No incorporar dependencias externas distintas de Vite.
5. Mantener Vite exclusivamente en `devDependencies`.
6. Utilizar una versión de Vite compatible con Node.js disponible en el entorno.
7. Utilizar la configuración predeterminada de Vite si es suficiente.
8. No crear directorios o archivos de sistemas futuros.
9. No realizar abstracciones innecesarias.
10. No modificar documentación ni archivos fuera de la lista autorizada.
11. No modificar, sobrescribir, eliminar, reemplazar ni renombrar archivos existentes.
12. No instalar herramientas adicionales.
13. No modificar la configuración global de OpenCode ni del entorno.
14. No realizar cambios en GitHub Issues, Milestones o Projects.
15. No realizar commits ni publicar cambios sin autorización expresa.
16. Limitar la instalación de dependencias a las declaradas y autorizadas en esta SPEC. Si npm requiere modificar un archivo existente o generar cambios fuera del alcance autorizado, el agente debe detenerse y reportarlo.

### Repository preflight

Antes de realizar cualquier modificación, el agente debe:

- Verificar la raíz del repositorio.
- Consultar `git status --short`.
- Inspeccionar los archivos y directorios relacionados con el alcance de esta SPEC.
- Comprobar si alguno de los archivos autorizados ya existe.
- Consultar la versión de Node.js disponible.
- Determinar una versión compatible de Vite.

Si existe algún archivo autorizado previamente, un cambio local pendiente o un conflicto que impida cumplir esta SPEC sin modificar contenido existente, el agente debe detenerse y comunicarlo al Project Owner.

No debe resolver conflictos por iniciativa propia.

---

# 10. Validation Strategy

## 10.1. Validation Scope

Se verificará:

- Estructura física y archivos autorizados.
- Configuración de `package.json`.
- Compatibilidad de Vite con Node.js.
- Definición y ejecución de scripts npm.
- Punto de entrada HTML5.
- Importación CSS desde JavaScript.
- Orden de importación de las capas CSS.
- Generación y consistencia de `package-lock.json`.
- Exclusiones de `.gitignore`.
- Funcionamiento del servidor de desarrollo.
- Carga de la aplicación en navegador.
- Construcción de producción.

## 10.2. Validation Tools

Herramientas autorizadas:

- Terminal o PowerShell.
- npm.
- Node.js.
- Vite.
- Navegador web.

Comandos principales:

```powershell
node --version
npm --version
npm install
npm run dev
npm run build
```

El servidor de desarrollo deberá iniciarse utilizando el script definido en `package.json`.

Se verificará la URL local indicada por Vite. El puerto predeterminado es 5173, aunque Vite puede seleccionar otro si el puerto está ocupado.

## 10.3. Validation Procedure

1. Verificar la estructura y los archivos creados.
2. Comprobar que `package.json` respeta las restricciones de dependencias.
3. Comprobar que `package-lock.json` es consistente.
4. Ejecutar `npm run dev`.
5. Acceder a la aplicación desde el navegador.
6. Comprobar que no existen errores de carga atribuibles a la estructura inicial.
7. Detener el servidor de desarrollo.
8. Ejecutar `npm run build`.
9. Comprobar que la carpeta `dist/` fue generada.
10. Verificar las exclusiones de `.gitignore`.
11. Revisar `git status --short` y confirmar que no existen modificaciones fuera del alcance autorizado.

## 10.4. Stopping Conditions

La validación finaliza cuando:

- Todos los criterios de aceptación están verificados.
- El servidor de desarrollo funciona.
- La aplicación carga correctamente en el navegador.
- La construcción de producción finaliza correctamente.
- La estructura física respeta los archivos autorizados.
- No existen modificaciones fuera del alcance aprobado.

Si se encuentra un error que requiere ampliar el alcance, incorporar dependencias o modificar archivos no autorizados, el agente debe detenerse y reportarlo.

No debe improvisar soluciones fuera de esta SPEC.

---

# 11. Definition of Done

## 11.1. Definition of Done — SPEC

La especificación se considera completa para revisión cuando:

- El objetivo está claramente definido.
- El alcance incluido y excluido está delimitado.
- Los requisitos funcionales y técnicos son verificables.
- Los criterios de aceptación son objetivos y no presentan solapamientos innecesarios.
- Los archivos y operaciones autorizados están identificados explícitamente.
- Las restricciones de implementación están documentadas.
- La estrategia de validación permite verificar los criterios.
- Los seis principios INVEST están evaluados como PASS.
- El documento respeta las decisiones aprobadas del proyecto.

La aprobación corresponde exclusivamente al Project Owner.

## 11.2. Definition of Done — Implementation

La implementación se considera completa cuando:

- Todos los criterios de aceptación AC-01 a AC-11 están verificados y aprobados.
- La estructura física coincide con los archivos autorizados.
- Vite funciona en desarrollo y producción.
- La aplicación carga correctamente en el navegador.
- JavaScript y CSS respetan la organización establecida.
- No se implementó funcionalidad del juego.
- No se introdujeron dependencias no autorizadas.
- No se modificaron archivos fuera del alcance aprobado.
- La validación fue ejecutada y sus resultados están documentados.
- El Project Owner revisó y aceptó el resultado.

La finalización técnica de la implementación no equivale a la aceptación del Project Owner.

---

# 12. Expected Deliverables

## 12.1. Configuration

- `package.json`
- `package-lock.json`
- `.gitignore`

## 12.2. Application Entry Points

- `index.html`
- `src/index.js`
- `src/main.css`

## 12.3. CSS Structure

- `src/styles/base.css`
- `src/styles/tokens.css`
- `src/styles/layout.css`
- `src/styles/components.css`
- `src/styles/sections.css`
- `src/styles/utilities.css`

## 12.4. Verified Technical Capabilities

- Servidor de desarrollo local funcional.
- Carga correcta de la aplicación en navegador.
- Construcción de producción generada en `dist/`.
- Dependencias reproducibles mediante `package-lock.json`.

No se espera que el juego tenga funcionalidad operativa al finalizar esta SPEC.

---

# 13. Risks and Open Questions

| ID | Risk | Mitigation | Status |
|---|---|---|---|
| R-01 | La versión de Node.js podría no ser compatible con la versión elegida de Vite. | Inspeccionar Node.js antes de seleccionar Vite y utilizar una versión compatible. | Controlled |
| R-02 | Algunos archivos autorizados podrían existir previamente o contener cambios locales. | Ejecutar repository preflight y detenerse ante conflictos. | Controlled |
| R-03 | La creación prematura de directorios de sistemas futuros podría generar estructura innecesaria. | Limitar la creación a los archivos autorizados. | Resolved |
| R-04 | La falta de separación CSS podría dificultar futuras implementaciones visuales. | Establecer seis archivos con responsabilidades diferenciadas y orden obligatorio de importación. | Resolved |
| R-05 | El puerto predeterminado de Vite podría encontrarse ocupado. | Utilizar la URL y el puerto informados por Vite. | Controlled |
| R-06 | Los archivos generados podrían incorporarse accidentalmente al control de versiones. | Configurar y verificar `.gitignore`. | Controlled |

No existen preguntas abiertas que requieran redefinir la arquitectura o el alcance de esta SPEC.

---

# 14. INVEST Evaluation

| Principle | Evaluation | Justification |
|---|---|---|
| Independent | PASS | La estructura inicial no depende de sistemas funcionales del juego. Las dependencias externas se limitan a Vite como herramienta de desarrollo. |
| Negotiable | PASS | Se definen resultados técnicos y restricciones aprobadas, permitiendo decisiones de implementación menores mientras no alteren el alcance ni la arquitectura. |
| Valuable | PASS | Proporciona una base técnica ejecutable y modular para el desarrollo incremental del juego. |
| Estimable | PASS | El alcance está delimitado mediante una lista cerrada de archivos, operaciones, dependencias y verificaciones. La compatibilidad de versiones se resuelve durante el preflight sin modificar el alcance. |
| Small | PASS | La especificación se limita a la estructura física inicial y la configuración básica de Vite, sin implementar sistemas del juego ni interfaz definitiva. |
| Testable | PASS | Cada resultado tiene criterios verificables mediante inspección de archivos, terminal y navegador. |

**Overall result: PASS**

La evaluación considera exclusivamente el alcance definido en esta especificación. La inspección del repositorio y la comprobación de compatibilidad del entorno son actividades obligatorias de preimplementación, no justificaciones para ampliar el alcance.

---

# 15. Execution Report

Esta sección debe completarse únicamente después de la implementación autorizada.

## 15.1. Implementation Summary

Pendiente.

## 15.2. Files Created

Pendiente.

## 15.3. Acceptance Criteria Results

| Criterion | Result | Evidence |
|---|---|---|
| AC-01 | Pending | |
| AC-02 | Pending | |
| AC-03 | Pending | |
| AC-04 | Pending | |
| AC-05 | Pending | |
| AC-06 | Pending | |
| AC-07 | Pending | |
| AC-08 | Pending | |
| AC-09 | Pending | |
| AC-10 | Pending | |
| AC-11 | Pending | |

## 15.4. Validation Results

Pendiente.

## 15.5. Deviations and Blockers

Pendiente.

## 15.6. Final Status

Pendiente de validación y aceptación del Project Owner.

---

**Project Owner Authority**

Esta especificación no constituye autorización de implementación por sí misma.

La implementación solo podrá comenzar cuando:

1. El Project Owner apruebe formalmente SPEC-003.
2. El Project Owner otorgue autorización expresa para implementar su alcance.

Ningún agente puede aprobar su propia especificación ni considerar aprobada la implementación sin aceptación del Project Owner.
