# Nivel 12

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
