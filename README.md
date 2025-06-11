# Guía para hacer un _Fork_ y _Pull-Request_
Esta pequeña guía está centrada en enseñar a utilizar el _fork_ y crear _pull-requests_ para la entrega de Trabajos Prácticos fuera de término.

Primero vamos a ver qué es cada uno y luego el cómo se hacen.

# Definiciones
## Fork
En GitHub, un fork es una manera de hacer una copia de un repositorio en la cuenta del usuario. 
Esto es útil para cuando queramos entregar trabajos fuera del plazo de entrega.

## Pull-Request
Los Pull-request son solicitudes de cambio hechas por los colaboradores para solicitar cambios dentro de una rama. Estas solicitudes muestran las diferencias entre el contenido de la rama de origen y el contenido de la rama de destino.

## ¿Por qué usar esta combinación?
Luego de la fecha de entrega establecida para cada práctico, los repositorios se cierran y no se admiten nuevos
commits, por lo que podemos hacer un _fork_ del repositorio, hacer las correcciones y luego hacer un Pull-Request
para que puedan ser corregidas por el docente.

# Tutorial

## Cómo hacer un _Fork_ (desde GitHub)
Primero nos vamos a dirigir al repositorio que queramos copiar a nuestra cuenta. Una vez allí vamos a ir al botón que dice "Fork":

![1-](1.png)

Esto nos redirige al apartado de creación del fork. Acá se nos explica brevemente en qué consiste y podemos cambiar el nombre, la descripción y el dueño del fork (puede ser más de uno). 

![2-](2.png)

Con todo esto armado, podemos crear la copia y automáticamente GitHub nos va a llevar al nuevo repositorio.

![3](3.png)

## Trabajando en el _Fork_ 

Podemos trabajar en las copias de dos formas

### Clonando el repositorio

Con el repositorio ya creado, solamente resta clonarlo en una nueva carpeta y comenzar a trabajar en él. 
Como es una copia, los _commits_ y los _pushes_ no van a ir al repositorio original.
En todo caso, podemos verificarlo usando el comando en _Bash_
```bash
git remote -v
```
Este comando nos va a devolver la siguiente salida
```
origin  https://github.com/usuario/nombre-repositorio-forkeado.git (fetch)
origin  https://github.com/usuario/nombre-repositorio-forkeado.git (push)
```
### Reemplazando la URL del repositorio ya clonado
Otra forma de trabajar con nuestro fork es tomando la carpeta donde estábamos trabajando antes de que se cierre el repositorio y cambiarle la URL donde van nuestros cambios.

1. Para esto tenemos que abrir _Bash_ en la carpeta donde estamos trabajando.
2. Luego vamos a nuestro fork y copiamos la URL para poder trabajar en ella. 

Una vez copiado, volvemos al _Bash_ y ponemos el siguiente comando con nuestra URL:
```bash
git remote set-url origin https://github.com/usuario/nombre-repositorio-forkeado.git
```
Ahora verificamos si se cambió la dirección
```bash
git remote -v
```

Esperando el Output:
```
origin  https://github.com/usuario/nombre-repositorio-forkeado.git (fetch)
origin  https://github.com/usuario/nombre-repositorio-forkeado.git (push)
```

**Con cualquiera de los dos métodos, ya podemos empezar a subir nuestros _commits_ y _pushes_ al _fork_.**

## Haciendo un Pull-Request
Para hacer un Pull-Request tenemos que ir a la pestaña con el mismo nombre dentro de nuestro repositorio.
![pr](4.png)
Acá vamos a crear un nuevo Pull-Request
![4-](5.png)
Después, clickeamos en _compare across forks_
![5-](6.png)
Vamos a ver que nos salen las opciones _base repository_ _base: main_ y _head repository_ _compare: main:_
- En la primera opción vamos a seleccionar el nombre del repositorio original
- En _head repository_ seleccionamos el nombre de nuestro fork
Debajo van a aparecer todos los commits que hicimos y el botón de "Create pull request"
![6](7.png)
Creamos el Pull-Request y lo subimos.
![7](8.png)

Luego de todo eso, pueden cargar el repositorio en el formulario de entrega 
(no olviden aclarar que la entrega es en un Pull request separado)

Y listo, así de sencillo es hacer un Pull-Request en GitHub.

## Último paso
Hacer la entrega con [el formulario](https://dub.sh/p2/entregas) con la dirección del repositorio en el que creamos el PR.

## Sincronizando tu Fork con el repositorio original

Es posible que el repositorio original reciba cambios después de que hiciste tu fork. Para mantener tu fork actualizado y evitar conflictos, es recomendable sincronizarlo periódicamente con el repositorio original. Aquí tienes los pasos para hacerlo:

Aunque esto es raro en el contexto del uso que le damos a git y GitHub, es interesante tenerlo en cuenta ya que posibilita que utilicemos esta mecánica para sumar contribuciones a cualquier otro repositorio de la plataforma.

1. **Agregar el repositorio original como remoto**
   
   Abre una terminal en la carpeta de tu fork y ejecuta:
   ```bash
   git remote add upstream https://github.com/OWNER_ORIGINAL/REPO_ORIGINAL.git

Reemplaza OWNER_ORIGINAL y REPO_ORIGINAL por el usuario y nombre del repositorio original.

Puedes verificar que se agregó correctamente con:

```bash
git remote -v
```

Deberías ver algo como:

```Code
origin    https://github.com/tu_usuario/tu_fork.git (fetch)
origin    https://github.com/tu_usuario/tu_fork.git (push)
upstream  https://github.com/OWNER_ORIGINAL/REPO_ORIGINAL.git (fetch)
upstream  https://github.com/OWNER_ORIGINAL/REPO_ORIGINAL.git (push)
```
2. Traer los cambios del repositorio original

    Ejecuta:
```bash
git fetch upstream
```

3. Fusionar los cambios en tu rama principal

Cambia a tu rama principal (usualmente llamada main):

```bash
git checkout main
```

Fusiona los cambios del repositorio original:

```bash
git merge upstream/main
```

Si hay conflictos, Git te lo indicará y deberás resolverlos antes de continuar.

Subir los cambios a tu fork en GitHub

Finalmente, sube los cambios a tu fork:

```bash
git push origin main
```
    
¡Listo! Así mantienes tu fork actualizado con el repositorio original. Se recomienda hacerlo antes de comenzar nuevas tareas o antes de crear un Pull Request.

# Créditos

@gonabur a quien armó la base de este apunte.

Se aceptan pull requests
