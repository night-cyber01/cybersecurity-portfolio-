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
