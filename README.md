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