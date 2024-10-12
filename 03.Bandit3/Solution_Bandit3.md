# Bandit3

The password for the next level is stored in a hidden file in the **inhere** directory.

---

**Flag**

```bash
password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

# Conexión

```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
```

---

# Solución

En este problema usaremos el comando `cd`para cambiar de carpeta `inhere`y luego realizaremos los pasos que ya hemos ido siguiendo hasta ahora, aunque abra una variación en los parámetros del listado de archivos:

## Cambiar de directorio

Primero listaremos los archivos para estar seguros de los archivos que se encuentran en bandit3:

```bash
bandit3@bandit:~$ ls -l
total 4
drwxr-xr-x 2 root root 4096 Sep 19 07:08 inhere
```

Y bueno, hemos comprobado que solo hay un directorio y es el mismo del enunciado, por lo tanto, accedemos a el:

```bash
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ 
```

---

## Listar archivos

Una vez que accedimos al nuevo directorio, listaremos los archivos:

```bash
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ 
```

**¿Qué ha pasado? ¿Dónde está el archivo?** Bueno, el archivo esta oculto y para revelarlo deberemos incluir el parámetro `-a` nuestro listado, con el fin de mostrar el archivo oculto que empieza por `.`

```bash
bandit3@bandit:~/inhere$ ls -la
total 12
drwxr-xr-x 2 root    root    4096 Sep 19 07:08 .
drwxr-xr-x 3 root    root    4096 Sep 19 07:08 ..
-rw-r----- 1 bandit4 bandit3   33 Sep 19 07:08 ...Hiding-From-You
```

Finalmente hemos podido revelar al archivo secreto que contiene nuestra `flag`

---

## Mostrar el contenido de un archivo

Y no hay mucha ciencia a continuación, solo debemos usar un `cat`:

```bash
bandit3@bandit:~/inhere$ cat ...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

---

## 4️⃣[Bandit4](https://github.com/Groppoxx/OverTheWire-Bandits-Solution/blob/main/04.Bandit4/Solution_Bandit4.md)

```bash
password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```