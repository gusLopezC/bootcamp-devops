
# Manual Práctico de Git

## 1. Introducción a Git
Git es un sistema de control de versiones distribuido, ampliamente utilizado para gestionar proyectos de software. A través de este manual, aprenderás a usar las funcionalidades básicas y avanzadas de Git para gestionar ramas, colaborar con equipos y mantener la historia del proyecto clara y organizada.

---

## 2. Ejercicio 1: Instalar Git
Si no tienes Git instalado, sigue la guía oficial de instalación:

- [Guía de instalación de Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

---

## 3. Ejercicio 2: Configurar Git

Una vez que hayas instalado Git, debes configurarlo con tu nombre y correo:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@dominio.com"
```

Verifica la configuración:

```bash
git config --list
```

---

## 4. Ejercicio 3: Inicializar un repositorio Git

1. Crea un nuevo directorio para tu proyecto:

    ```bash
    mkdir mi-proyecto
    cd mi-proyecto
    ```

2. Inicializa Git en el directorio:

    ```bash
    git init
    ```

3. Añade un archivo y realiza tu primer commit:

    ```bash
    echo "# Mi Proyecto" > README.md
    git add README.md
    git commit -m "Primer commit: agregar README"
    ```

---

## 5. Ejercicio 4: Clonar un repositorio existente

Clona un repositorio desde GitHub o cualquier otro sistema de control de versiones remoto:

```bash
git clone https://github.com/usuario/repositorio.git
```

---

## 6. Ejercicio 5: Trabajar con ramas

1. Crea una nueva rama para desarrollar una funcionalidad:

    ```bash
    git checkout -b mi-rama
    ```

2. Realiza los cambios en la rama y añade los archivos al stage:

    ```bash
    git add .
    ```

3. Realiza un commit con un mensaje descriptivo:

    ```bash
    git commit -m "Añadir nueva funcionalidad"
    ```

4. Cambia de rama, por ejemplo, a `main`:

    ```bash
    git checkout main
    ```

5. Fusiona los cambios de la rama en `main`:

    ```bash
    git merge mi-rama
    ```

---

## 7. Ejercicio 6: Resolver conflictos de merge

1. Si hay conflictos, Git te lo indicará durante el `merge`.

2. Edita los archivos conflictivos para resolver los conflictos manualmente. Busca las marcas `<<<<<<<`, `=======`, y `>>>>>>>`.

3. Después de resolver los conflictos, añade los archivos corregidos:

    ```bash
    git add archivo_conflictivo
    ```

4. Completa la fusión:

    ```bash
    git commit
    ```

---

## 8. Ejercicio 7: Subir cambios a un repositorio remoto

1. Conecta tu repositorio local a uno remoto:

    ```bash
    git remote add origin https://github.com/usuario/repositorio.git
    ```

2. Sube los cambios:

    ```bash
    git push -u origin main
    ```

3. Para futuras actualizaciones, solo necesitas ejecutar:

    ```bash
    git push
    ```

---

## 9. Ejercicio 8: Descargar cambios del repositorio remoto

Para actualizar tu repositorio local con los cambios remotos:

```bash
git pull origin main
```

Si estás trabajando en otra rama, ajusta el comando a esa rama:

```bash
git pull origin mi-rama
```

---

## 10. Ejercicio 9: Eliminar ramas locales y remotas

1. Después de fusionar una rama, puedes eliminarla localmente:

    ```bash
    git branch -d mi-rama
    ```

2. Si necesitas forzar la eliminación (si no fue fusionada):

    ```bash
    git branch -D mi-rama
    ```

3. Para eliminar una rama remota:

    ```bash
    git push origin --delete mi-rama
    ```

---

## 11. Ejercicio 10: Inspeccionar el historial de commits

1. Para ver el historial de commits:

    ```bash
    git log
    ```

2. Para un historial más compacto:

    ```bash
    git log --oneline
    ```

3. Para ver los cambios en un archivo específico:

    ```bash
    git log -p archivo.txt
    ```

---

## 12. Ejercicio 11: Deshacer cambios

1. Si has hecho cambios en un archivo pero aún no los has añadido al stage, puedes revertirlo:

    ```bash
    git checkout -- archivo.txt
    ```

2. Si ya añadiste los cambios al stage y quieres eliminarlos del stage:

    ```bash
    git reset HEAD archivo.txt
    ```

3. Para deshacer el último commit (manteniendo los cambios en el working directory):

    ```bash
    git reset --soft HEAD^
    ```

4. Para deshacer el último commit y eliminar los cambios:

    ```bash
    git reset --hard HEAD^
    ```

---

## 13. Ejercicio 12: Trabajar con tags

1. Crea un tag para marcar una versión específica del proyecto:

    ```bash
    git tag v1.0.0
    ```

2. Sube el tag al repositorio remoto:

    ```bash
    git push origin v1.0.0
    ```

---

## 14. Ejercicio 13: Ignorar archivos con `.gitignore`

1. Crea un archivo `.gitignore` en el directorio raíz del proyecto.

2. Añade los archivos o directorios que quieres ignorar. Por ejemplo:

    ```
    node_modules/
    *.log
    ```

3. Los archivos listados en `.gitignore` no serán seguidos ni subidos a Git.

---

## 15. Ejercicio 14: Revertir un commit

Si un commit introdujo un error, puedes revertirlo sin cambiar el historial anterior:

```bash
git revert <id_commit>
```

Esto creará un nuevo commit que deshace los cambios del commit especificado.

---

## Conclusión

Este manual cubre los conceptos esenciales de Git, desde la creación de repositorios, el trabajo con ramas, hasta la gestión de conflictos y el uso de etiquetas. Con práctica, serás capaz de gestionar proyectos de manera eficiente con Git.
