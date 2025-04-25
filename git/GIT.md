# Git Command Reference

Una guía completa de comandos de Git, segmentados por temas para fácil consulta.

---

## 🔄 Configuración Inicial

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu.email@example.com"
git config --global core.editor "nano"
git config --list
```

## 🗒️ Creación de Repositorios

```bash
git init                 # Inicializa un repositorio local
```

## 🗂️✨ Clonación de Repositorios

```bash
git clone <url>          # Clona un repositorio remoto
```

## 🔹 Estados de los Archivos

```bash
git status               # Verifica el estado del repositorio
```

## 📂 Agregar Cambios

```bash
git add <archivo>        # Agrega un archivo al staging area
git add .                # Agrega todos los archivos al staging area
```

## 📚 Confirmar Cambios (Commit)

```bash
git commit -m "Mensaje"  # Realiza un commit
```

## 🚌 Enviar Cambios al Remoto

```bash
git push                 # Envía cambios al repositorio remoto
git push origin <rama>    # Envía una rama específica
```

## 🚧 Obtener Cambios del Remoto

```bash
git pull                 # Trae y fusiona cambios
```

## ✍️ Sincronizar Ramas Eliminadas en Remoto

```bash
git fetch --prune        # Elimina referencias locales de ramas eliminadas en el remoto

# Activar automáticamente:
git config --global fetch.prune true
```

## 🖋️ Manejo de Ramas

```bash
git branch               # Lista ramas locales
git branch <nombre>       # Crea nueva rama
git checkout <rama>       # Cambia de rama
git checkout -b <rama>    # Crea y cambia de rama
git merge <rama>          # Fusiona una rama a la actual
git branch -d <rama>      # Borra una rama local
git push origin --delete <rama> # Borra una rama remota
```

## 🗓️ Visualización de Historial

```bash
git log                  # Muestra el historial de commits
git log --oneline         # Historial resumido
```

## 🔹 Ignorar Archivos

Crear archivo `.gitignore` y agregar patrones de archivos/directorios a ignorar.

```bash
# Ejemplo
node_modules/
.env
*.log
```

## 🔹 Stash (Guardar Cambios Temporales)

```bash
git stash                # Guarda cambios actuales de forma temporal
git stash list           # Lista stashes guardados
git stash apply          # Aplica último stash
git stash pop            # Aplica y elimina último stash
```

## 🔹 Comparar Cambios

```bash
git diff                 # Muestra diferencias no staged
git diff --staged         # Muestra diferencias staged
```

## 🔹 Etiquetas (Tags)

```bash
git tag                  # Lista etiquetas
git tag <nombre>          # Crea una etiqueta ligera
git tag -a <nombre> -m "mensaje"  # Crea etiqueta anotada
git push origin <nombre>  # Envía etiqueta al remoto
git push --tags           # Envía todas las etiquetas
```

## 💡 Deshacer Cambios

```bash
git reset <archivo>       # Saca archivo del staging area
git checkout -- <archivo> # Revierte cambios en un archivo
```

## 🔹 Revertir Commits

```bash
git revert <commit>       # Crea nuevo commit que revierte otro commit
git reset --hard <commit> # Restablece todo el árbol de trabajo a un commit anterior (con cuidado)
```

## 🔹 Manejo de Remotos

```bash
git remote add origin <url>  # Agrega un remoto
git remote -v              # Lista remotos
```

## 🔹 Rebase

```bash
git rebase <rama>          # Reescribe historial de cambios sobre otra base
```

## 🔹 Submódulos

```bash
git submodule add <url> <ruta> # Agrega un submódulo
```

## 🗓️ Hooks

Ubicados en `.git/hooks/`. Ejemplos: `pre-commit`, `pre-push`, `post-merge`.

---

# Git Flow

`git flow` es una extensión de Git que define un modelo de trabajo basado en ramas:

| Rama         | Propósito                        |
|--------------|-----------------------------------|
| `main`       | Código en producción               |
| `develop`    | Código de desarrollo estable       |
| `feature/*`  | Nuevas funcionalidades             |
| `release/*`  | Preparación de versiones           |
| `hotfix/*`   | Corrección de errores críticos     |

**Principales comandos de git-flow:**

```bash
git flow init              # Inicializa flujo en tu repositorio
git flow feature start <nombre>   # Iniciar una nueva feature
git flow feature finish <nombre>  # Finalizar una feature
git flow release start <version>  # Iniciar un release
git flow release finish <version> # Finalizar un release
git flow hotfix start <nombre>    # Iniciar un hotfix
git flow hotfix finish <nombre>   # Finalizar un hotfix
```

---

# Fin del documento

✨ Espero que esta guía te sirva como referencia rápida para tus proyectos de Git. ✨

