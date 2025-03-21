<h1 align="center">  Niveles 11 - 15</h1>
<br>

```admonish info title='Recomendaciones'
¡Vas a empezar niveles más difíciles! 

<span style="color: hotpink">Recuerda tomar descansos!</span>
```

## Nivel 11

Decodifica el contenido de data.txt con ROT13

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

Ahora copia la contraseña para acceder al siguiente nivel.


<hr>
<br>

## Nivel 12

Configura tu entorno de trabajo.

```Bash
cd /tmp | mktemp -d
```

El resultado del anterior comando deberás usarlo par ir a esa dirección:

```bash
 cd /tmp/tmp.OI1B9JR1PW
```

Una vez en el directorio temporal copia el archivo data.txt y renombralo sin extensión para un mejor manejo

```Bash
 cp ~/data.txt hexdump
```

Revertir el hexdump

```Bash
xxd -r hexdump compfile
```

Vamos a verificar los primeros bits del hexadecimal, esto nos dará el tipo de archivo en el que estamos trabajando, para eso tenemos que usar el siguiente comando: 

```Bash
xxd compfile| head
```

Cambiaremos el nombre del archivo para añadirle la extensón que le corresponda

```Bash
mv compfile compfile.gz
```

Ahora a descomprimir

```Bash
 gzip -d compfile.gz
```

Verificaremos nuevamente el encabezado hexadecimal

```Bash
xxd compfile| head
```

Añadiremos la extensión **.bz2** 

```Bash
mv compfile compfile.bz2
```

Descomprime

```Bash
bzip2 -d compfile.bz2
```

Cambia la extensión y vuelve a descomprimir

```Bash
mv compfile compfile.gz | gzip -d compfile.gz
```

Verificamos el encabezado hexadecimal nuevamente.

Cambiamos la extensión y descomprimimos:

```Bash
 mv compfile compfile.tar | tar -xf compfile.tar
```

Vemos que el resultado anterior fue un archivo nuevo llamado data5.bin

Verificamos el encabezado del nuevo archivo

Lo procedemos a extraer:

```Bash
 tar -xf data5.bin
```

Vemos que el resultado anterior fue un archivo nuevo llamado data6.bin

Verificamos el encabezado del nuevo archivo

Lo procedemos a renombrar y a extraer:

```Bash
mv data6.bin data6.bz2 | bzip2 -d data6.bz2
```

Verificamos el encabezado del resultado anterior

Lo procedemos a renombrar y a extraer:

```bash
 mv data6 data6.tar | tar -xf data6.tar
```

Verificamos el encabezado del resultado anterior

Lo procedemos a renombrar y a extraer:

```bash
 mv data8.bin data8.gz| gzip -d data8.gz
```

Ahora abriremos el ultimo resultado:

```bash
cat data8
```

Ahora copia la contraseña para acceder al siguiente nivel.

<hr>
<br>

## Nivel 13

Usaremos una llave privada para acceder al siguiente nivel.

Dentro del nivel 13 poner el siguiente comando:

```bash
ssh -i sshkey.private bandit14@bandit.labs.overthewire.or
g -p 2220
```

<hr>
<br>

## Nivel 14

Abriremos la contraseña del nivel actual:

```bash
 cat /etc/bandit_pass/bandit14
```

Ahora vamos a copiar el resultado anterior

Mandaremos la información al localhost en puerto 30000

```bash
nc localhost 30000
```

**Pega aquí la contraseña del primer paso**

 

Ahora copia la contraseña para acceder al siguiente nivel.

<hr>
<br>

## Nivel 15

Enviaremos la contraseña de este nivel al localhost en puerto 30001 usando encriptación SSL/TLS:

```bash
openssl s_client -connect localhost:30001
```

**Pega aquí la contraseña actual**

Ahora copia la contraseña para acceder al siguiente nivel.

<hr>
<br>

```admonish tip title='_Felicidades !!!!!!!_'
Superaste una etapa _desafiante_ <span style="color: hotpink">vamos por más! 🔥</span>
```