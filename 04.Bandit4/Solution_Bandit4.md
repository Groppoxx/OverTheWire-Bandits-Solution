# Bandit4

The password for the next level is stored in the only human-readable file in the **inhere** directory. Tip: if your terminal is messed up, try the “reset” command.

---

**Flag**

```bash
password: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

# Conexión

```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
```

---

# Solución

A partir de este punto para la solución de los problemas deberemos usar nuevos comandos, además abran distintas formas de resolver los problemas, por ello, te invito a que seas creativo en tus soluciones, por mi parte seré más breve con los comandos que ya conocemos.

## Cambiar de directorio

Primero listamos los archivos y/o directorios:

```bash
bandit4@bandit:~$ ls -l
total 4
drwxr-xr-x 2 root root 4096 Sep 19 07:08 inhere
```

Luego accedemos al directorio:

```bash
bandit4@bandit:~$ cd inhere
bandit4@bandit:~/inhere$
```

---

## Listar archivos

Ahora listaremos todos los archivos, hasta lo ocultos:

```bash
bandit4@bandit:~/inhere$ ls -la
total 48
drwxr-xr-x 2 root    root    4096 Sep 19 07:08 .
drwxr-xr-x 3 root    root    4096 Sep 19 07:08 ..
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file00
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file01
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file02
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file03
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file04
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file05
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file06
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file07
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file08
-rw-r----- 1 bandit5 bandit4   33 Sep 19 07:08 -file09
```

Se observa que hay muchos archivos que empiezan con `-` y ninguno oculto, tendremos que leerlos.

---

## Mostrar el contenido de un archivo (FALLIDO)

Debemos considerar que en el enunciado del problema mencionan que el archivo que tiene la contraseña es `human-readable`, esto significa que el contenido del archivo es legible y su contenido no está codificado o es ilegible.

```bash
bandit4@bandit:~/inhere$ cat ./-file00
�p��&�y�,�(jo�.at�:uf�^���@
```

<aside>
💡

Nótese que use `./` ya que estos archivos tienen el nombre con el mismo formato que el problema de `bandit1` , recuerda que leerlo sin`./` podría confundir al sistema.

</aside>

Al leer el primer archivo notamos que su contenido esta codificado, por lo tanto, puede que todos los archivos sean similares, podríamos probar uno por uno hasta encontrar el indicado, pero ¿Y si tuviéramos más de mil archivos? ¿Crees que sería correcto ir uno por uno revisando su contenido? 

---

## Determinar el tipo de archivo

Hay un comando interesante para este paso, el cual es `file` y nos permite determinar el tipo de archivo basándose en su contenido:

```bash
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```

Y como pueden ver use un comodín llamado **wildcard** y conocido por su carácter`*` , este me permite representar uno o más caracteres en un directorio basados en su nombre.

## Mostrar el contenido de un archivo (EXITOSO)

Finalmente podemos leer el archivo que por contenido tiene **ASCII text:**

```bash
bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

Lo interesante de este problema es que pudimos aprender un nuevo comando para determinar el tipo de archivo y utilizar un comodín que será nuestra nueva herramienta para resolver próximos problemas.

---

## 5️⃣[Bandit5](https://github.com/Groppoxx/OverTheWire-Bandits-Solution/blob/main/05.Bandit5/Solution_Bandit5.md)

```bash
password: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```