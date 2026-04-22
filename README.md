# Trabajo Individual git

Jhosua Alejandro Bustillos Calderon

##Clase 1

###¿QUE ES GIT?

Sistema de control de versiones

###¿COMO DESCARGAR GIT?

```
sudo pacman -Sy git
```

###¿COMO CONFIGURAR GIT?
```
git config user.name 
git config user.email
```

==================================================================

##Clase 2

###States and Commits

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
####Commits Conventions
Comitear commits atomicos, de max. 50 caracteres en INGLES con el uso de Add, Fix,
Change y Remove. Usar Prefijos como feat, docs, test, fix, refactor...

###Comandos nuevos
	
	- git restore arch.ext/  / --stage
	- git reset --soft
	- git log --online
	- git commit --amend -m  

