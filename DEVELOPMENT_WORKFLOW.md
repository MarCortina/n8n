# Flujo de Trabajo de Desarrollo - n8n Fork

## Estrategia de Branches

### Ramas Principales

- **`master`**: Mantiene sincronización con `n8n-io/n8n`. Solo se actualiza desde upstream.
- **`develop`**: Rama base para desarrollo de customizaciones.
- **`feature/*`**: Ramas para nuevas funcionalidades.
- **`fix/*`**: Ramas para correcciones de bugs.

## Workflow Diario

### 1. Actualizar desde n8n original

```bash
# Actualizar master con cambios de n8n-io/n8n
git checkout master
git fetch upstream
git merge upstream/master
git push origin master

# Actualizar develop con master
git checkout develop
git merge master
git push origin develop
```

### 2. Crear una nueva feature

```bash
# Crear rama desde develop
git checkout develop
git checkout -b feature/nombre-descriptivo

# Hacer cambios
# ...

# Commit
git add .
git commit -m "feat(componente): descripción del cambio"

# Push
git push origin feature/nombre-descriptivo
```

### 3. Merge a develop

```bash
git checkout develop
git merge feature/nombre-descriptivo
git push origin develop
```

## Convenciones de Commits

Seguimos [Conventional Commits](https://www.conventionalcommits.org/):

- `feat(scope): descripción` - Nueva funcionalidad
- `fix(scope): descripción` - Corrección de bug
- `docs(scope): descripción` - Cambios en documentación
- `refactor(scope): descripción` - Refactorización
- `test(scope): descripción` - Tests
- `chore(scope): descripción` - Tareas de mantenimiento

## Construcción y Testing

### Compilar un paquete específico

```bash
cd packages/nodes-base
pnpm build
```

### Compilar todo el proyecto

```bash
# Con más memoria si es necesario
export NODE_OPTIONS="--max-old-space-size=8192"
pnpm build
```

### Ejecutar n8n en desarrollo

```bash
pnpm start
# O con túnel
./packages/cli/bin/n8n start --tunnel
```

## Configuración Git

```bash
# Configurar usuario (local al repositorio)
git config user.email "tu@email.com"
git config user.name "Tu Nombre"
```

## Remotes Configurados

- `origin`: https://github.com/MarCortina/n8n.git (tu fork)
- `upstream`: https://github.com/n8n-io/n8n.git (repositorio original)
