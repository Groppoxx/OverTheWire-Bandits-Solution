# Bandit2

The password for the next level is stored in a file called **spaces in this filename** located in the home directory

---

**Flag**

```bash
password: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

# Conexión

```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

---

# Solución

Puesto que ya hemos realizado la solución de un problema similar en bandit1, los pasos serán similares:

## Listar archivos

Empezaremos listan los archivos:

```bash
bandit2@bandit:~$ ls -l
total 4
-rw-r----- 1 bandit3 bandit2 33 Sep 19 07:08 spaces in this filename
```

Se observa al inicio del listo que el tipo de archivo es `-`, esto sugiere que es un archivo (en caso sea `d` ser un directorio).

---

## Mostrar el contenido de un archivo

Como es un archivo y en usuario sale el permiso `r`, entonces podremos realizar un `cat`:

```bash
bandit2@bandit:~$ cat "spaces in this filename" 
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

<aside>
💡

Nótese que utilice comillas `” “`, esto me permite leer archivos con espacios en su nombre, ya que se interpretara como una única cadena de caracteres y no como archivos separados.

</aside>

---

## 3️⃣[Bandit3](https://github.com/Groppoxx/OverTheWire-Bandits-Solution/blob/main/03.Bandit3/Solution_Bandit3.md)

```bash
password: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```