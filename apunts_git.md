Git és un sistema de control de versions. (VCS)

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

El missatge del "commit" l'iniciem amb una paraula diferent segons si els canvis tenen a veure amb
- Arreglar errors
```bash
$ git commit -m "fix: "
```
- Noves característiques
```bash
$ git commit -m "feat: "
```
- Millora del codi
```bash
$ git commit -m "refactor: "
```



## Veure el llistat de commits
```bash
$ git log
```

# Conceptes bàsics

## Carpeta .git

- Tenim una carpeta amb uns arxius els quals volem incloure en un repositori.
- El repositori és una carpeta anomenada .git, la qual conté l'històric de canvis de tots els arxius.
- Aquesta carpeta .git es troba també en la carpeta on hi ha els arxius i és d'aquests dels que crea l'històric.
- Si moc la carpeta .git deixarà de tenir en el repositori els arxius anteriors i passarà a tenir els que es trobin en la nova carpeta on l'has deixat.

## Arxiu .gitignore

- Arxiu que conté els noms dels arxius que volem que Git ignori (queda fora del repositori i per tant del control de versions).


## Working tree
L'estat dels arxius que es troben en la carpeta on hi ha el repositori de Git.

## Remote
Un o més repositoris que es troben en el núvol i que estan sincronitzats amb el repositori local. Amb aquest repositori interactuem a partir de les comandes push i pull (fetch + merge).

Aquest repositori remote permet que varis usuaris puguin compartir-lo i treballar conjuntament.


# Comandes per Remote

Totes les comandes següents s'executen des de la terminal situada en la carpeta on hi ha el repositori local.


## Veure el llistat de repositoris remots

```bash
$ git remote -v
```

## Vincular el repositori local amb el remote

```bash
$ git remote add <nom del remote> <url del repositori remot propocionada per GitHub> 
```

Per exemple 

```bash
$ git remote add origin https://github.com/ditcas/apunts_python.git
```

## Actualitzar el remote pujant tots els nous commits

```bash
$ git push <nom del remote> <nom de la branca>
```

## Actualitzar el local amb els nous commits del remote

```bash
$ git pull <nom del remote> <nom de la branca>
```

# Iniciar un repositori local

```bash
$ git init .  # Inicia el repositori en la carpeta on es troba la terminal.
```

# Branques

- Per defecte hi ha una branca inicial, anomenada "main", a vegades "master".

- Per veure la branca en la que s'està treballant
```bash
$ git branch
o
$ git status
```

- Per crear i moure't a la vegada a aquella branca
```bash
$ git checkout -b <nom de la branca>
```

- Per moure't entre branques
```bash
$ git switch <nom de la branca a la que vols anar>
o
$ git checkout <nom de la branca a la que vols anar>
```

Aleshores el Finder mostra els arxius contemplant els commits fets a aquesta branca.

- Ajuntar una branca a una altra
Ens situem a la branca sobre la que volem incorporar els commit

```bash
$ git merge <nom de la branca que volem ajuntar>
```

> Git merge requereix un commit del merge (el fa automàtic) i cal escriure el missatge. Per defecte s'obre l'editor de text (Vim) amb el següent text "Merge branch <nom de la branca>". Per acceptar-lo, fem "Escape", ":" i "wq".

- Per esborrar una branca

Des de qualsevol branca que no sigui la que volem esborrar.

```bash
$ git branch -d <nom de la branca que volem esborrar>
```

- Quan crees un arxiu mentre no fas "commit" no s'adjudica el canvi a cap branca perquè de moment només està en el working tree.

- Quan fas una modificació a un arxiu mentre no has fet "commit" qualsevol canvi entre branques no serà possible.

# Claus SSH

Claus (una privada i una pública) que poden ser usades en diverses eines que demanen una interacció amb l'usuari, i permeten certificar la identitat de l'usuari.

- Vols enviar uns canvis (push) al remote. Si ho sol·licitem fent ús de les claus SSH, la clau privada (única i intransferible) encripta la informació que volem enviar.
- El receptor té la nostra clau pública (enllaçada inequívocament amb la clau privada) i intentarà desencriptar la informació. Si pot fer-ho, a part de tenir la informació, haurà certificat que erem nosaltres qui li enviavem, doncs sinó la clau no li hauria funcionat.
- Un cop desencriptada, executararia el push de la informació rebuda.

Les claus estan guardades en la carpeta del meu usuari, dins una carpeta oculta .ssh. L'extensió .pub indica que és la clau pública.

- Quan creem un repositori local de Git, dins la carpeta .git hi ha un arxiu anomenat "config". Des de la terminal, podem veure'l fent cat config, o modificar-lo fent nano config. Aquí és on indicarem que volem relacionar-nos a través de claus ssh.

# Clone vs Fork

- Quan clonem un repositori, fem una còpia dels arxius en el nostre directori, però no genera un repositori de Git. És a dir, en GitHub tenim accés de només lectura (no podem fer push ni pull contra ell, doncs pertany al seu creador. Seria com un accés directe al repositori del creador.)
- Si fem un Fork, passem a tenir una còpia d'aquell repositori en un repositori propi de GitHub. Aleshores podem fer un Clone del nostre repositori de GitHub i passarem a tenir els arxius en el nostre directori lligats a aquest remote. 
