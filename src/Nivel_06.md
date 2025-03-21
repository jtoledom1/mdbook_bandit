<h1 align="center">  Niveles 06 - 10</h1>
<br>
 
```admonish info title='Recomendaciones'
Recuerda revisar el apartado de <span style="color: hotpink">tareas!</span>
```

## Nivel 06

Busca el archivo que tenga las características descritas en Bandit

```bash
find /* -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

```bash
cat ./inhere/maybehere07/.file2
```

Ahora guarda la contraseña para pasar al siguiente nivel


<hr>
<br>

## Nivel 07

Abre el archivo data txt y busca la coincidencia  con la palabra millionth

```bash
cat data.txt| grep millionth
```

Ahora copia la contraseña para acceder al siguiente nivel.

<hr>
<br>
 
## Nivel 08

Para este nivel abre data.txt  ordenalo y busca la única lina que ocurre una sola vez.

```Bash
cat data.txt | sort | uniq -u
```

Ahora copia la contraseña para acceder al siguiente nivel.

<hr>
<br>
 
## Nivel 09

Abre data.txt filtrando el contenido por contenido legible por el humano, después busca los signos `'==='`


```Bash
strings data.txt | grep ==
```

Ahora copia la contraseña para acceder al siguiente nivel. 

<hr>
<br>
 
## Nivel 10

Decodifica el contenido base64 de data.txt

```Bash
 cat data.txt | base64 -d
```

Ahora copia la contraseña para acceder al siguiente nivel. 

<hr>
<br>

```admonish tip title='_Felicidades por pasar_ los <i>primeros 10 niveles!</i>'
Si estás leyendo sigue trabajando duro  _y_  <span style="color: hotpink">vamos por más!</span>.
```

