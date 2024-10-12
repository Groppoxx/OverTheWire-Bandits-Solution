# Bandit5

The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable

---

**Flag**

```bash
password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

# Conexión

```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
```

---

# Solución

Para este problema hay varios detalles que tenemos que tener en cuenta, pero eso no lo hace complejo, para encontrar la `flag` usaremos un nuevo comando `find` junto a sus distintos parámetros para cubrir las propiedades que tiene el archivo.

## Cambiar de directorio

Listamos los archivos y/o directorios:

```bash
bandit5@bandit:~$ ls -l
total 4
drwxr-x--- 22 root bandit5 4096 Sep 19 07:08 inhere
```

Accedemos al directorio:

```bash
bandit5@bandit:~$ cd inhere/
bandit5@bandit:~/inhere$
```

---

## Listar archivos

Ahora listaremos todos los archivos:

```bash
bandit5@bandit:~/inhere$ ls -l
total 80
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere00
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere01
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere02
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere03
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere04
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere05
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere06
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere07
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere08
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere09
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere10
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere11
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere12
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere13
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere14
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere15
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere16
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere17
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere18
drwxr-x--- 2 root bandit5 4096 Sep 19 07:08 maybehere19
```

Por lo visto todos son directorios y dentro de ellos seguro hay varios archivos, por lo tanto, es momento de usar nuestro nuevo comando.

---

## Buscar archivo

Usaremos el comando `find` para buscar entre los archivos y directorios el que deseemos, en este caso con las siguientes propiedades expresadas en parámetros:

```bash
bandit5@bandit:~/inhere$ find ./* -type f -size 1033c ! -executable
./maybehere07/.file2
```

<aside>
💡

Los parametros usados son:

- `-type f`: Especificar que estamos buscando un archivo.
- `-size 1033c`: Especificamos el tamaño del archivo, ósea su peso, la `c` seria lo mismo a `bytes`.
- `! -executable`: Especificar que el archivo no es ejecutable.
</aside>

También existe otra manera de resolverlo y solo usaremos el `ls` :

```bash
bandit5@bandit:~/inhere$ ls ./* -la | grep 1033
-rw-r-----  1 root bandit5 1033 Sep 19 07:08 .file2
```

Ahora que conocemos el nombre del archivo que coincide con el peso, pero no sabemos en qué directorio esta por lo tanto podemos listarlo otra vez, pero solo los archivos de nombre `.file2`

```bash
bandit5@bandit:~/inhere$ ls ./*/.file2 -l | grep 1033
-rw-r----- 1 root bandit5 1033 Sep 19 07:08 ./maybehere07/.file2
```

<aside>
💡

Si bien hemos usado el comando para listar archivos, se agregó el `grep`, el cual permite filtrar por una cadena de caracteres, en este caso estoy filtrando por su peso, ya que al listar archivos con los parámetros `-l` los estoy ordenando y obteniendo datos extras.

</aside>

---

## Mostrar el contenido de un archivo

Ya que conocemos su ruta absoluta, podemos mostrar su contenido:

```bash
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

Con este problema hemos visto dos formas de solucionarlo curiosas y a su vez útiles en nuestro aprendizaje continuo.

---

## 6️⃣[Bandit6](https://github.com/Groppoxx/OverTheWire-Bandits-Solution.git)

```bash
password: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```