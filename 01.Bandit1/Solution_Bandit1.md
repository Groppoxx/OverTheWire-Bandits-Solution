# Bandit1

The password for the next level is stored in a file called **-** located in the home directory

---

Por si no lo recuerdas, aquí te dejo la `flag` (contraseña) que encontramos el nivel anterior:

```bash
password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

# Conexión

Nos encontramos en un nuevo nivel y establecer nuestra conexión será una tarea que repetiremos constantemente:

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

---

# Solución

**¡Comencemos!** Es probable que, si aún no has explorado cómo funciona Linux, te sientas un poco estancado en este nivel. Pero no te desanimes; aprender sobre la marcha puede hacer que la información se asiente mejor en nuestra memoria.

## Listar archivos

Empezaremos listan los archivos, usando el comando que aprendimos en el nivel 0:

```bash
bandit1@bandit:~$ ls -l
total 4
-rw-r----- 1 bandit2 bandit1 33 Sep 19 07:08 -
```

Podemos observar que hay un archivo llamado `-` , que nombre más raro, tratemos leerlo.

---

## Mostrar el contenido de un archivo (FALLIDO)

```bash
bandit1@bandit:~$ cat -
```

No está mostrándome su contenido, parece que la consola espera algo, ¿a qué se deberá?, presionare `ctrl + c` para cancelar la ejecución de mi comando y procederé a explicarte lo siguiente:

<aside>
💡

Si nos ponemos a pensar unos segundos, no te parece que el nombre del archivo es igual al **símbolo guión** que usamos en el parámetro de **listar archivos** (`-l`).

</aside>

### ¿Por qué no puedo ver el contenido de un archivo con un nombre especial?

Si, tal y como lo vez, el nombre del archivo que contiene la `flag` es igual al símbolo que se usa para realizar la acción de un comando. Entonces, ¿qué deberíamos hacer?

Para evitar esta confusión, hay un par de soluciones sencillas:

- **Especificar la ruta relativa o absoluta**
    - **Ruta relativa:** Esta es la ubicación del archivo en relación con nuestro directorio actual. Por ejemplo:
        
        ```bash
        bandit1@bandit:~$ pwd
        /home/bandit1
        ```
        
        Actualmente estoy en `/home/bandit1`. Para acceder a un archivo en esta carpeta, puedo usar su nombre directamente (`cat -`). Sin embargo, esto no nos funcionó, por lo tanto, usaremos `./` para que la terminal lo reconozca correctamente. Así, le indico que está en el directorio actual y evito que lo confunda con una opción.
        
        ```bash
        bandit1@bandit:~$ cat ./-
        ```
        
        <aside>
        💡
        
        Marea un poco, lo entiendo, pero es fácil de entender, solo debemos tener en cuenta lo siguiente:
        
        - `./`: Representa el directorio actual. Lo usamos cuando queremos referirnos a un archivo o carpeta que se encuentra en el mismo directorio en el que estamos trabajando
        - `../`: Representa el directorio padre, es decir, el nivel superior en la jerarquía de carpetas. Lo utilizamos para acceder a archivos o carpetas que están un nivel arriba del directorio actual.
        </aside>
        
    - **Rutas Absolutas:** Es la dirección completa del archivo, comenzando desde la raíz del sistema de archivos. Por ejemplo:
        
        ```bash
        bandit1@bandit:~$ cat /home/bandit1/-
        ```
        

---

## Mostrar el contenido de un archivo (EXITOSO)

Realizaremos uno de los 2 comandos vistos en la sección anterior, ambos nos permitirán ver la respuesta, pero usaremos el de la **ruta relativa**, ya que al usar la ruta relativa estaremos escribiendo una dirección más corta y específica hacia el archivo que queremos accede

```bash
bandit1@bandit:~$ cat ./-                                                     
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

<aside>
💡

Finalmente, fuimos capaces de obtener la `flag` y aprendimos cómo utilizar rutas relativas en la terminal de manera efectiva.

</aside>

---

## 2️⃣[Bandit2](https://github.com/Groppoxx/OverTheWire-Bandits-Solution.git)

```bash
password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```