___

> <font color="#00b050">🚀 Essential Commands </font>

Identificarte con user,email.. para el autor de los cambios que se realicen

```
git config --global user.name "user"
git config --global user.mail "user@gmail.com"
```

Configuración de usuario de Git como el user, email, passphrase..

```
cat ~/home/user/.gitconfig
```

Editar la configuración global de usuario directamente en el archivo de configuración

```
git config --global --edit
```

Inicializar una carpeta como un repositorio de Git

```
git init
```

Archivos de configuración, historial.. de Git

```
ls ~/git-project/.git
```

Personalizar el nombre de la rama principal

```
# cambiar el nombre de la rama principal
git branch -m branch-name 

# cambiar el nombre de la rama principal forzadamente
git branch -M branch-name 
```

Indica el estado en el que se encuentra un proyecto como rama actual, commits..

```
git status
```

Agregar uno o varios ficheros para empezar a trabajar con ellos con Git

```
git add hellogit.py
```

Agregar un comentario al commit inicial mediante un editor de texto como nano/vim..

```
git commit
```

Realizar una "captura" del proyecto agregando un comentario directamente en el comando

```
git commit -m "Este es mi primer commit :)"
```

Mostrar logs de los commits realizados

```
# Logs de commits o acciones hechas de manera más visual
git log --graph

# Logs de commits de manera más visual y compacta
git log --graph --pretty=oneline

# Logs de commits de manera más corta
git log --graph --decorate --all --oneline

# Alias de un comando, se puede ver en .gitconfig
git config --global alias.tree "log --graph --decorate --all --oneline"
```

Revertir cambios al ultimo commit hecho del archivo

```
git checkout hellogit2.py
```

Lista los archivos que estén en estado modificado

```
git reset
```

Muestra una comparación de cambios en caso de que los haya

```
git diff
```

Realizar un rollback a otro commit, podemos revertirlo usando el mismo comando cambiando el id

```
git checkout commit-hash-id
```

Volver a un estado previo específico, se descartan los cambios que hubieran por encima

```
git reset --hard commit-hash-id
```

Historial completo de interacciones realizadas

```
git reflog
```

Dar una etiqueta al commit más reciente

```
git tag tag-name
```

Muestra los tags creados en el repositorio

```
git tag
```

Moverse (mover el HEAD) entre commits con tags, debe tener un tag el commit al que te muevas

```
git checkout tags/tag-name
```

Deshacer cambios, crea un nuevo commit que hace lo contrario a los cambios que quieres eliminar

```
git revert commit-hash-id
```

Crear una nueva rama

```
git branch branch-name
```

Moverse entre ramas

```
git switch branch-name
```

Combinar cambios de la rama en la que estas con otra, además hay que agregar un comentario

```
git merge branch-name
```

Un commit temporal, util para guardar cambios temporalmente y cambiar de rama

```
git stash
```

Muestra información de commits stash pendientes

```
git stash list
```

Recuperar los cambios del stash

```
git stash pop
```

Eliminar los cambios del stash

```
git stash drop
```

Eliminamos una rama específica

```
git branch -d branch-name
```

Descarga el historial del repo sin los cambios

```
git fetch
```

Descarga el historial del repo con los cambios

```
git pull
```

Agregar un repo de github

```
git remote add origin git@github.com:user/hello-git.git
```

Establecer una técnica de merge, solo la primera vez

```
git config pull.rebase false
```

Descargar el historial con los cambios

```
git pull origin master
```

Subir los cambios

```
git push origin master
```

___

> <font color="#ff0000">⚡Powerful Commands! Use with caution! </font>

Sirve para elegir un commit específico de una rama y aplicarlo en tu rama actual, sin tener que traer toda la rama completa.

```
git cherry-pick commit-hash-id
```

Git busca el punto donde tu rama se separó de master, guarda tus cambios temporalmente, pone los nuevos cambios de master y luego vuelve a aplicar tus commits uno por uno encima de lo new.

```
git rebase branch-name
```

___