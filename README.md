# Trabajo Individual git

Jhosua Alejandro Bustillos Calderon

## Clase 1

### ¿QUE ES GIT?

Sistema de control de versiones

### ¿COMO DESCARGAR GIT?

```
sudo pacman -Sy git
```

### ¿COMO CONFIGURAR GIT?
```
git config user.name 
git config user.email
```

================================================================

## Clase 2

### States and Commits

	- Directorio de Trabajo
		Git solo observa lo creado y lo cataloga:
			* Untracked
			  NO se tiene una version previa de lo creado
			* Modified
			  Se tiene version previa para modificar o eliminar
	- Stage Area
		Un area de espera
			* git add archivo.ext/.
			  Para que Git conozca lo que se quiere guardar
			* git commit -m ""
			  Despues de add, para que Git indique un punto de guardado
#### Commits Conventions

Comitear commits atomicos, de max. 50 caracteres en INGLES con el uso de Add, Fix,
Change y Remove. Usar Prefijos como feat, docs, test, fix, refactor...

### Comandos nuevos
```
 git restore arch.ext/  / --stage
 git reset --soft
 git log --online
 git commit --amend -m  
```

================================================================

## Clase 3

###Configurar SSH
Key para autenticar commits
```
ssh -keygen -t ed25519 "correo de uso en github"
```

Abrir la direccion que devuelve en donde se almaceno la SSH y copiar la SSH dada

En github:
	- Ir a Settings
	- Crear nuev SSH
	- Dar un title
	- Pegar la SSH
	- Crear Key

Probar:
```
ssh -T git@github.com
```

###Conectar local con remoto
```
git remote add origin git@github:... .git
git branch -m main
git push -m origin main
```
================================================================

## Clase 4

### Multiples SSH

```
ssh -keygen -t ed25519 -t "correo" -f "direccion ssh"
```

Comando para crear otra llave ssh.

Para configurarla, se nesecita crear archivo config y poner:
```
#Cuenta Personal
Host github.com
	Hostname github.com
	User git
	IdentifyFile "direccion de ssh"

#Cuenta Otra
Host github.nuevo
	Hostname github.com
	User git
	IdentifyFile "direccion de ssh nueva"
```

### Git Checkout

Permite ver y cambiarse a otros commits pasados.
```
git checkout hashDelCommit
```

Cmd para que el HEAD no apunte a tu rama, si no al commit.

Entramos a un estado Detached

NO pasa nada si se hace un git add y commit al estar en el commit viejo, el commit simplemente no se guarda,
para guardar es mejor crear una rama para este commit.

================================================================

## Clase 5

### Ramas

Comandos necesarios:

```
git branch
```
Para ver en que rama te encuentras.
```
git branch feature/example
```
Crear una rama a partir de main.

```
git branch -D nombre-rama
```
Elimnar una rama.

```
git checkout
```
Verificar estado de la rama actual.

```
git checkout -b nombre-rama
```
Crear una nueva rama y cambiarse a esa rama a la vez.

```
git switch
```
Cambiar rama

### Un poco de Git Flow

La rama MAIN, solo debe contener codigo que funciona teniendo solo un commt inicial.

La rama DEV tiene codigo en pre-produccion y de ésta rama salen las otras ramas.

Una rama FEATURE contiene una nueva caracterisitca/funcionalidad del programa o sistema.

```
feature/add-new-function
```

Tras terminar con una rama FEATURE, es decir, mergear a la rama DEV lo que se hizo en FEATURE, se debe de borrar dicha RAMA.

================================================================

## Clase 6

### Trabajar en Ramas

```
git merge
```
Permite fusionar nuestras ramas.

```
git fetch
```
Permite ver si hubo cambios en la rama y sus ramas hijas, tambien actualiza si es que se crearon nuevas ramas.

```
git pull
```
Permite traer todos los cambios que tiene el repositorio remoto de esa rama.

```
git push
```
Sube tus cambios al repositorio remoto de esa rama.

### Flujos de Trabajo

#### Sin Pull Request
git checkout develop
git fetch
git pull origin develop
git checkout rama # Agregas -b si estás creando la rama
git merge develop # Solo si hubo cambios en develop
###### Trabajas en tu rama
git push origin rama # Agregas -u si es la primera vez que subes cambios al repositorio remoto
git checkout develop
git fetch
git pull origin develop
git merge –no-ff rama
###### Resuelves manualmente los archivos fallidos y sus conflictos
git add .
git commit
[Ctrl + O, Enter, Ctrl + X](depende si usan nano)
git branch -D rama
git push origin develop

#### Con Pull Request
git checkout develop
git fetch
git pull origin develop
git checkout rama # Agregas -b si estás creando la rama
git merge develop # Solo si hubo cambios en develop
###### Trabajas en tu rama
git push origin rama # Agregas -u si es la primera vez que subes cambios al repositorio remoto
git checkout develop
git fetch
git pull origin develop
git merge –no-ff rama
###### Resuelves manualmente los archivos fallidos y sus conflictos
git add .
git commit
[Ctrl + O, Enter, Ctrl + X](depende si usan nano)
git branch -D rama
git push origin develop

================================================================

## Clase 7

### Pull Request
Es la forma profesional de trabajar con git/github, crea un request en el grupo del repositorio en github que permite ver que se quiere mergear o unir al código base que ya se tiene.

### Crear un PR?
Para ello primero una vez que hagas git push origin rama debes dirigirte a github.com y seguir los pasos del siguiente tutorial
https://youtu.be/4CeMKqloOJc 

### Flujo de trabajo (Con Pull Requests)
git checkout develop
git fetch
git pull origin develop
git checkout rama # Agregas -b si estás creando la rama
git merge develop # Solo si hubo cambios en develop
#### Trabajas en tu rama
git push origin rama # Agregas -u si es la primera vez que subes cambios al repositorio remoto
git checkout develop
git fetch
git checkout rama
git merge develop # Solo si hubo cambios en develop antes de hacer la PR
#### Resuelves manualmente los archivos fallidos y sus conflictos
git add .
git commit
[Ctrl + O, Enter, Ctrl + X](depende si usan nano)
git push origin rama
#### Sigues el flujo mostrado en “¿Cómo crear un PR?

### Uso de los PRs
Los usamos por temas de seguridad, que cualquier colaborador pueda tocar nuestro repositorio y mergear sin preguntar o avisar es un riesgo constante, ¿Y si lo hace mal? ¿Y si está metiendo código malicioso? ¿Y si es un norcoreano intentando hackearme que solo se ganó mi confianza? ¿Qué código está pusheando?

Los PRs permite al equipo y lo fuerza a ver los cambios, limita la colaboración y obliga al debate y deliberación. Nos permite entender que vamos a poner en marcha, quien lo hara, presentar una opinión u oponerse al cambio, los PRs nos permiten un mejor manejo grupal de nuestro repositorio en equipo

### Proteger mi repo
Bien, ya sabemos la importancia de los PRs pero aun así, no hemos limitado nada, seguimos confiando en que nuestros colaboradores esperaran nuestra review y aprobación para unir su código, pero aún pueden hacerlo, porque no los hemos limitado, para eso lo que debemos hacer es lo que se detalla en el siguiente video corto:
https://youtu.be/ZdLomug2-UQ 


### Colaborar proyecto son ser invitado
En la clase nuestro querido postulante Andre colaboró sin estar invitado en nuestro repositorio sin estar invitado, esto es posible y nos lo explica él mismo en el siguiente video:
[En progreso]

