### Nivel 0 → Nivel 1
- **Contraseña obtenida**: bandit0
- **Método**: Lectura del archivo `readme` en el directorio home
- **Nueva contraseña**: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
- **Concepto aprendido**: Lectura básica de archivos en Linux usando `cat`
- **Comando ejecutado**: `cat readme`
- **Output observado**:
bandit0@bandit:~$ ls -la total 24 drwxr-xr-x 2 root root 4096 Oct 14 09:25 . drwxr-xr-x 150 root root 4096 Oct 14 09:29 .. -rw-r--r-- 1 root root 220 Mar 31 2024 .bash_logout -rw-r--r-- 1 root root 3851 Oct 14 09:19 .bashrc -rw-r--r-- 1 root root 807 Mar 31 2024 .profile -rw-r----- 1 bandit1 bandit0 438 Oct 14 09:25 readme

bandit0@bandit:~$ cat readme Congratulations on your first steps into the bandit game!! Please make sure you have read the rules at https://overthewire.org/rules/ If you are following a course, workshop, walkthrough or other educational activity, please inform the instructor about the rules as well and encourage them to contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

- **Análisis**: 
- El archivo `readme` tiene permisos `-rw-r-----` (lectura para owner y group)
- El owner es `bandit1` y el group es `bandit0`, lo que indica que el siguiente nivel será `bandit1`
- Este es el nivel introductorio que enseña fundamentos de navegación en Linux
### Nivel 1 → Nivel 2
- **Contraseña obtenida**: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
- **Método**: Lectura del archivo con nombre especial `-`
- **Nueva contraseña**: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
- **Concepto aprendido**: Manejo de nombres de archivo especiales en Linux
- **Comando ejecutado**: `cat ./-`
- **Output observado**:
bandit1@bandit:~$ ls -la total 24 drwxr-xr-x 2 root root 4096 Oct 14 09:25 . drwxr-xr-x 150 root root 4096 Oct 14 09:29 .. -rw-r--r-- 1 root root 220 Mar 31 2024 .bash_logout -rw-r--r-- 1 root root 3851 Oct 14 09:19 .bashrc -rw-r--r-- 1 root root 807 Mar 31 2024 .profile -rw-r----- 1 bandit2 bandit1 33 Oct 14 09:25 -

bandit1@bandit:~$ cat ./- 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

- **Análisis técnico**:
- El archivo se llama literalmente `-` (un solo guion)
- En Unix/Linux, `-` es un carácter especial que representa stdin
- Para leer archivos con nombres especiales, se usa `./` para especificar ruta relativa
- Este es un concepto **crítico** en ciberseguridad: atacantes a menudo usan nombres de archivo especiales para ocultar malware
- **Lección de seguridad**: Siempre usar comillas o prefijos (`./`) con nombres de archivo no confiables
