# Comandes bàsiques

Totes les comandes següents s'executen des de la terminal situada en la carpeta on hi ha el repositori local.

## Estat actual del repositori local

```bash
$ git status
```

## Afegir arxius a l'àrea de stage - unstaged files to staged files

```bash
$ git add <name_file> <name_file2>

$ git add . # afegir tots els arxius
```

## Confirmar que els canvis fets en els arxius de l'àrea stage succeeixin també en el repositori local 

```bash
$ git commit -m "message"  # -m indica message
```

# Conceptes bàsics

## Carpeta .git

- Tenim una carpeta amb uns arxius els quals volem incloure en un repositori.
- El repositori és una carpeta anomenada .git, la qual conté l'històric de canvis de tots els arxius.
- Aquesta carpeta .git es troba també en la carpeta on hi ha els arxius i és d'aquests dels que crea l'històric.
- Si moc la carpeta .git deixarà de tenir en el repositori els arxius anteriors i passarà a tenir els que es trobin en la nova carpeta on l'has deixat.

## Working tree
L'estat dels arxius que es troben en la carpeta on hi ha el repositori de Git.

## Remote
Un o més repositoris que es troben en el núvol i que estan sincronitzats amb el repositori local. Amb aquest repositori interactuem a partir de les comandes push i pull (fetch + merge).

Aquest repositori remote permet que varis usuaris puguin compartir-lo i treballar conjuntament.


# Comandes per Remote

Totes les comandes següents s'executen des de la terminal situada en la carpeta on hi ha el repositori local.

```bash
$ git remote -v # Veure el llistat de repositoris remots

$ git remote add <nom del remote> <url del repositori remot propocionada per GitHub> # Vincula el repositori local amb el remote.
```

Per exemple 

```bash
$ git remote add origin https://github.com/ditcas/apunts_python.git
```