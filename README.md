# Mejores prácticas de git
Repositorio enfocado en los desarrolladores para mejorar el tiempo y el proceso al realizar la subida de cambios a ramas principales del repositorio. Seguir los siguientes pasos:

## Pasos para optimizar los comandos git add, git commit y git push:
- Registrar como alias el siguiente comando, utilizado para obtener la rama actual.
```bash
git config --global alias.currentBranch '!f() { git symbolic-ref --short -q HEAD; }; f'
```
- Registrar como alias el siguiente comando, que son utlizados para hacer el git add, git commit y git push.
```bash
git config --global alias.acp '!f() { git add . && git commit -m "$@" && git push -u origin $currentBranch; }; f'
```
>Considerar que el alias ```acp``` es la abreviación de ```add```,```commit```y```push```

## Para corregir el error del git push
Al realizar el ```git push -u origin branch``` y 
La rama actual no tiene una rama upstream. Por lo tanto, solo está creando una nueva rama en la computadora local.
![](https://raw.githubusercontent.com/DominicVillanueva/custom-commands/main/error_push.png)
### Solución
El siguiente comando corregirá el error y siempre creará una rama remota que rastrea la rama local.
```bash
git config --global push.default current
```