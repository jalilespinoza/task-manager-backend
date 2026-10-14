# Explicación de `tsconfig.json`

El archivo `tsconfig.json` contiene la configuración del compilador de TypeScript. Define cómo se analizan los archivos `.ts`, qué versión de JavaScript se genera y en qué carpeta se guardan los archivos compilados.

## Configuración actual

```jsonc
{
  // tsconfig.json. Opciones de compilación de TypeScript
  "compilerOptions": {
    "target": "ES2022",
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "rootDir": "src",
    "outDir": "dist",
    "strict": true,
    "noUncheckedIndexedAccess": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "types": ["node"],
  },
  "include": ["src/**/*.ts"],
  "exclude": ["node_modules", "dist"],
}
```

## `compilerOptions`

Estas propiedades controlan el proceso de compilación.

| Propiedad                        | Descripción                                                                                         |
| -------------------------------- | --------------------------------------------------------------------------------------------------- |
| `target: "ES2022"`               | Indica que el JavaScript generado debe ser compatible con ECMAScript 2022.                          |
| `module: "NodeNext"`             | Configura el sistema de módulos moderno de Node.js, compatible con `import` y `export`.             |
| `moduleResolution: "NodeNext"`   | Define cómo TypeScript busca módulos y paquetes siguiendo las reglas de Node.js.                    |
| `rootDir: "src"`                 | Establece `src` como la carpeta raíz del código fuente.                                             |
| `outDir: "dist"`                 | Guarda en `dist` los archivos JavaScript generados por TypeScript.                                  |
| `strict: true`                   | Activa las comprobaciones estrictas de tipos para detectar más errores durante el desarrollo.       |
| `noUncheckedIndexedAccess: true` | Considera que un acceso mediante índice puede devolver `undefined`.                                 |
| `esModuleInterop: true`          | Mejora la interoperabilidad entre módulos CommonJS y módulos ES.                                    |
| `skipLibCheck: true`             | Omite la comprobación de tipos de las declaraciones de librerías externas y acelera la compilación. |
| `types: ["node"]`                | Incluye los tipos de Node.js, como `process`, `fs` y `http`.                                        |

### Ejemplo de `noUncheckedIndexedAccess`

Con esta opción activada, TypeScript detecta que una posición podría no existir:

```ts
const tasks: string[] = [];
const task = tasks[0]; // string | undefined
```

Esto obliga a comprobar el valor antes de utilizarlo y ayuda a evitar errores durante la ejecución.

## `include`

```json
"include": ["src/**/*.ts"]
```

Indica que se deben analizar y compilar todos los archivos con extensión `.ts` ubicados dentro de `src` y sus subcarpetas.

Por ejemplo:

```text
src/index.ts
src/controllers/task-controller.ts
src/services/task-service.ts
```

## `exclude`

```json
"exclude": ["node_modules", "dist"]
```

Excluye del proceso de compilación:

- `node_modules`: dependencias instaladas por el gestor de paquetes.
- `dist`: archivos generados por una compilación anterior.

Esto evita analizar archivos que no forman parte del código fuente del proyecto.

## Flujo de compilación

El flujo esperado del proyecto es:

```text
Archivos TypeScript en src/
          |
          v
  Compilador de TypeScript
          |
          v
Archivos JavaScript en dist/
```

Para compilar el proyecto se puede ejecutar:

```bash
pnpm exec tsc
```

El comando utiliza automáticamente el archivo `tsconfig.json` de la raíz del proyecto.
