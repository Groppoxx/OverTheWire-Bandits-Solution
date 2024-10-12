# Bandit0

The password for the next level is stored in a file called **readme** located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

---

# Conexión

Nos conectaremos por `ssh` hacia el servidor:

```bash
ssh bandit0@bandit.labs.overthewire.org -p2220
```

- `bandit0` : Es el nombre de usuario para autenticarnos al servidor.
- `bandit.labs.overthewire.org`: Es el dominio al que nos queremos conectar, en algunos casos será la `IP` del servidor.

Luego de establecer conexión, la contraseña será el mismo nombre de usuario (almenos para este caso):

```bash
password: bandit0
```

---

# Solución

La solución para este primer nivel es sencilla, ya que solo requiere de 2 comandos muy conocidos:

## Listar archivos

```bash
bandit0@bandit:~$ ls -l
total 4
-rw-r----- 1 bandit1 bandit0 438 Sep 19 07:08 readme
```

En lo personal considero que listar archivos usando el parámetro de `-l` resulta muy útil, ya que nos permite ver detalles adicionales sobre los archivos y directorios (número de enlaces, el propietario, el grupo, el tamaño del archivo (en bytes) y la fecha de modificación).

<aside>
💡

Se observa un archivo con el nombre `readme`, el cual tiene permisos de lectura, por lo tanto, podemos visualizar su contenido.

</aside>

## Mostrar el contenido de un archivo

```bash
bandit0@bandit:~$ cat readme
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

Y bueno usar el comando `cat` nos permite visualizar el contenido de un archivo directamente en la terminal sin necesidad de abrirlo en un editor de texto.

<aside>
💡

Como resultado de nuestro esfuerzo logramos encontrar la `flag`, la cual nos permitió aprender comandos sencillos pero muy útiles que usaremos prácticamente todo el tiempo que pasemos en la consola

</aside>

---

## 1️⃣[Bandit1](https://github.com/Groppoxx/OverTheWire-Bandits-Solution/blob/main/01.Bandit1/Solution_Bandit1.md)

```bash
password: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```