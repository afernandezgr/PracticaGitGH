#Práctica GIT KC - Bootcamp Mobile VI

##- ¿Qué comando utilizaste en el paso 11? ¿Por qué?

```
git reset --hard HEAD~1
```

Este comando deshace el último commit realizado y lo que había en el Working Copy lo deja como estaba antes de realizarlo. El Staging Area queda vacío.
Mueve el puntero a HEAD -1 posición (commit justo anterior) y con el modificador hard provoca que se modique el working copy, sería equivalente a realizar un
git reset HEAD~1  + git checkout -- 

##- ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?

El commit ha desaparecido del git log pero aún podemos verlo usando git reflog
Podemos volver a ese commit con el comando git reset más el código del hash asociado que aparece al ejecutar el comando, con el modificador --hard provocamos que el Working Copy también se restaure, en caso contrario lo único que hariamos sería mover el punto del head a ese commit.

```git reflog
f5adf89 (HEAD -> styled, master) HEAD@{0}: reset: moving to HEAD~1
b080dea HEAD@{1}: commit: Modificación fichero git-nuestro.md en rama styled
f5adf89 (HEAD -> styled, master) HEAD@{2}: checkout: moving from master to styled
f5adf89 (HEAD -> styled, master) HEAD@{3}: commit (initial): Creación de fichero git-nuestro.md
```
Como vemos el hash b080dea corresponde al commit donde introdujimos el fichero modificado por lo cual lo dejariamos como antes, modificando el Working Copy


##- El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?
```git merge master```
Estando en la rama styled absorbemos a master.
No causó conflicto, da el mensaje 'Already up to date'. No habría nada que fusionar al ir 'styled' por delante, con lo cual la incluye.

##- El merge del paso 19, ¿Causó algún conflicto? ¿Por qué? 
Si, da conflicto, los ficheros difieren del que hay en la rama styled del de la otra rama htmlify. Ante la duda git avisa del posible conflicto para que este lo resuelvo usuario.

##- El merge del paso 21, ¿Causó algún conflicto? ¿Por qué? 
No ha causado conflicto. Hizo un fast-forward, una vez hemos resuelto los conflictos. La styled se encuentra por delante de las master, al hacer el merge lo que hacemos es mover el puntero de la rama 'master'

##- ¿Qué comando o comandos utilizaste en el paso 25?
```git log --graph ```  -> versión extendida

o bien 

```git log --graph --pretty=oneline``` --> versión reducida


##- El merge del paso 26, ¿Podría ser fast forward? ¿Por qué? 
Si podría ser un fast-forward porque los commits forman una 'línea', lo que hace el merge simplemente es avanzar hasta la rama absorbida, title. No tenemos el riesgo de perder ningun commit.


##- ¿Qué comando o comandos utilizaste en el paso 27?
```git reset HEAD~1```

##- ¿Qué comando o comandos utilizaste en el paso 28? 
```git checkout -- git-nuestro.md```

##- ¿Qué comando o comandos utilizaste en el paso 29?
Intentamos eliminar la rama title con 
```git branch -d title```
Pero da mensaje de error ya que los cambios de esa rama no están contenidos en ninguna otra. Lo forzamos con -D
```git branch -D title```

##- ¿Qué comando o comandos utilizaste en el paso 30? 

```git reflog```
Localizamos con el reflog el commit correspondiente al merge de ficheros de las dos ramas indicadas

```git reset --hard 4a02478```
Para dejar el working copy con el fichero con los cambio correctamente fusionado y no solamente con el puntero HEAD cambiado

##- ¿Qué comando o comandos usaste en el paso 32?
```git reflog``` -> buscamos el primer commit cuando se creo por primera vez el poema

```git reset --hard f5adf89```
El que aparece mas abajo del todo


##- ¿Qué comando o comandos usaste en el punto 33?
```git reflog``` -> buscamos el commit donde se hizo el merge de master con title con el modificador --hard para que modifique el working copy. El hecho de poner un buen mensaje de commit ayuda mucho a localizar los commit / reset / merge.

```git reset --hard 4a02478``` -> Restauramos a la posición indicado donde se ha fusionado el fichero con el titulo


