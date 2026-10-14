# Task Manager Backend

Backend de gestión de tareas desarrollado con TypeScript y ejecutado sobre Node.js.

## Requisitos

- Node.js 22 o una versión posterior.
- pnpm 11.

## Instalación

Instala las dependencias del proyecto desde la raíz:

```bash
pnpm install
```

Si pnpm informa que el script de compilación de `esbuild` fue ignorado, autoriza la dependencia con:

```bash
pnpm approve-builds
```

Selecciona `esbuild` y confirma la autorización.

## Comandos disponibles

| Comando | Descripción |
| --- | --- |
| `pnpm dev` | Inicia el proyecto en modo desarrollo y observa los cambios en `src/index.ts`. |
| `pnpm start` | Ejecuta el punto de entrada con `tsx`. |
| `pnpm check` | Comprueba los tipos sin generar archivos. |
| `pnpm build` | Compila TypeScript y genera los archivos JavaScript en `dist`. |
| `pnpm serve` | Ejecuta la versión compilada desde `dist/index.js`. |

## Flujo recomendado

Durante el desarrollo:

```bash
pnpm dev
```

Para comprobar y compilar el proyecto:

```bash
pnpm check
pnpm build
pnpm serve
```

## Estructura del proyecto

```text
task-manager-backend/
├── src/
│   ├── data/       # Datos de la aplicación
│   ├── models/     # Modelos y tipos del dominio
│   ├── services/   # Lógica de negocio
│   ├── utils/      # Funciones auxiliares
│   └── index.ts    # Punto de entrada
├── dist/           # JavaScript generado por la compilación
├── package.json    # Dependencias y scripts
├── pnpm-lock.yaml  # Versiones exactas de dependencias
├── tsconfig.json   # Configuración de TypeScript
└── TSCONFIG.md     # Explicación de la configuración de TypeScript
```

## Compilación de TypeScript

El código fuente se encuentra en `src` y los archivos generados se guardan en `dist`. La configuración completa del compilador se explica en [TSCONFIG.md](TSCONFIG.md).

## Estado del proyecto

El proyecto se encuentra en desarrollo. El script de pruebas aún no está implementado.
