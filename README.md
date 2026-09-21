<div align="center">

# University Vault

_Base de conocimiento personal para mi carrera universitaria_

[![Tool](https://img.shields.io/badge/Tool-Obsidian-7c3aed?labelColor=181825&style=for-the-badge&logo=obsidian&logoColor=white)](https://obsidian.md/)
[![Sync](https://img.shields.io/badge/Sync-Obsidian%20Git-f97316?labelColor=181825&style=for-the-badge&logo=git&logoColor=white)](https://github.com/Vinzent03/obsidian-git)
[![Format](https://img.shields.io/badge/Format-Markdown-1e293b?labelColor=181825&style=for-the-badge&logo=markdown&logoColor=white)](https://www.markdownguide.org/)
[![License](https://img.shields.io/github/license/Badjavii/university-vault?color=a6e3a1&labelColor=181825&style=for-the-badge)](./LICENSE)

</div>

## Sobre este vault

Este es mi vault personal de Obsidian para la universidad. Contiene apuntes de clase, resúmenes, ejercicios y referencias de cada materia que curso, en Markdown plano y versionado con git para no perder nada entre dispositivos ni entre semestres.

Los apuntes viven acá. **El código vive en otro lado**: cada materia que involucra programación tiene su propio repositorio bajo `~/Dev/University/<subject>/`, y los apuntes enlazan a esos repos con URLs absolutas de GitHub en vez de rutas locales. Así el vault se mantiene portable y puedo publicar los repos de código como públicos mientras el vault en sí permanece privado.

La sincronización la maneja el plugin de la comunidad [Obsidian Git](https://github.com/Vinzent03/obsidian-git), que hace auto-commit y push a un repositorio privado de GitHub cada cierto tiempo.

## Organización por semestres

El contenido está dividido en carpetas por semestre. Cada semestre tiene su propio `README.md` con la lista de materias cursadas ese período y los enlaces a los repos de código correspondientes.

| Semestre | Carpeta |
|---|---|
| Septiembre 2026 – Enero 2027 | [`sem-sep-jan-2026-2027/`](./sem-sep-jan-2026-2027/) |

A medida que avance la carrera se agregan nuevas carpetas de semestre sin tocar las anteriores. Los semestres viejos quedan como archivo consultable.

## Convenciones

### Nomenclatura de carpetas y archivos

Todos los nombres de carpetas y archivos van **en inglés y kebab-case**, en minúsculas y sin espacios. Esto es consistente con el naming de mis repositorios de código y evita problemas de escape en la terminal. El contenido de las notas sí va en español (o el idioma que corresponda al material).

- **Carpetas de semestre**: `sem-<mes-inicio>-<mes-fin>-<año-inicio>-<año-fin>/`, por ejemplo `sem-sep-jan-2026-2027/`.
- **Carpetas de materia**: `machine-learning/`, no `Machine Learning/`.
- **Apuntes de clase**: `W<semana>-D<día>-<tema>.md`, por ejemplo `W1-D2-intro-python.md`. Así quedan ordenados cronológicamente dentro de la carpeta de la materia.
- **Map of Content**: `MOC-<materia>.md` en la raíz de cada carpeta de materia, funciona como índice del tema.
- **Notas sueltas** (resúmenes, cheatsheets, prep de examen): nombres descriptivos en kebab-case, por ejemplo `cheatsheet-sql-joins.md`, `exam-prep-midterm.md`.

### Estructura de las notas

Cada nota empieza con un heading `#` que coincide con el tema del archivo. Los subheadings usan `##` y siguientes. El frontmatter YAML es opcional pero recomendado para tags y fechas en notas que planeo revisitar seguido.

### Enlaces

- Enlaces internos entre notas: sintaxis de Obsidian `[[wikilink]]`.
- Enlaces a código, commits o archivos de mis repos: **URLs absolutas de GitHub**, nunca rutas `file://` locales, para que el vault siga siendo portable entre máquinas.
- Referencias externas (papers, docs, artículos): Markdown link plano.

### Adjuntos

Las imágenes y otros adjuntos van en una subcarpeta `_attachments/` dentro de cada carpeta de materia, así viajan con las notas que los referencian y no ensucian la raíz del vault ni del semestre.

## Estructura del repositorio

```
university-vault/
├── .obsidian/                        # Config de Obsidian (versionada, excepto workspace/cache)
├── sem-sep-jan-2026-2027/
│   ├── README.md                     # Materias del semestre
│   ├── database-systems/
│   ├── machine-learning/
│   ├── offensive-cybersecurity/
│   └── quantum-software/
├── .gitignore
└── README.md
```

La carpeta `.obsidian/` se versiona para que los plugins, hotkeys, temas y snippets sean reproducibles en cualquier dispositivo. Solo se excluyen las partes efímeras (estado del workspace, cache, estado del graph view) vía `.gitignore`.

## Flujo de sincronización

1. Obsidian Git hace auto-commit cada 10 minutos y push al remote privado en GitHub.
2. Al arrancar, Obsidian hace pull de `main` para traer cambios hechos desde otro dispositivo.
3. Los commits manuales son bienvenidos para checkpoints con sentido (fin de una sesión de estudio, antes de un examen), con mensajes descriptivos.

Si dos dispositivos editan el vault al mismo tiempo, el conflicto se resuelve a mano desde la CLI: el plugin reporta el pull fallido y el merge se hace fuera de Obsidian para mantener el historial limpio.

## Créditos

Este vault lo mantiene **Badjavii**, estudiante de ciencias de la computación.
