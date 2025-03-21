# Niveles 0-5

## Nivel 0

### Acceso

*Para acceder al servidor usa las siguiete conexión ssh*

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

*La contraseña para tu primer nivel será:*

```
bandit0
```

A continuación abre el archivo readme 

```
cat readme
```

```admonish
Por último copia la clave para usarla para pasar al siguiente nivel.
```

<hr>
<br>

## Nivel 01

Para este nivel tienes que abrir el archivo '-'

```
cat <-
```

Copia la contraseña para acceder al siguiente nivel

<hr>
<br>
 
## Nivel 02
 
A continuación abre el archivo '**spaces in this filename**'

```bash
cat spaces \in \this \filename
```

Ahora copia la contraseña para acceder al siguiente nivel.

<hr>
<br>
 
## Nivel 03

A continuación cambia de ubicación a **inhere** 

```bash
cd inhere
```

Abre el archivo oculto 

```bash
 cat ...Hiding-From-You
```

Copia la contraseña para pasar al siguiente nivel.

<hr>
<br>
 
## Nivel 04

A continuación cambia de ubicación a **inhere**

```bash
cd inhere
```

Vamos a verificar los tipos de archivos que hay en el directorio actual

```bash
file ./*
```

Ahora tenemos que abrir el archivo que contiene formato tipo texto ASCII

```bash
cat <-file07
```

Ahora guarda la contraseña para pasar al siguiente nivel.

<hr>
<br>
 
## Nivel 05

Busca el archivo que tenga las características descritas en Bandit

```bash
find ./* -size 1033c -not -executable
```

Abre el archivo que coincida

```bash
cat ./inhere/maybehere07/.file2
```

Ahora guarda la contraseña para pasar al siguiente nivel
