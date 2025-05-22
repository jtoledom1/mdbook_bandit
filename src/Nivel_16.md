<h1 align="center">  Niveles 16 - 20</h1>

```admonish info title='Recomendaciones'
¡Vas a empezar niveles más difíciles! 

<span style="color: hotpink">Recuerda tomar descansos!</span>
```

## Nivel 16

Ahora, debemos tener a mano la contraseña que utilizamos para acceder a este nivel.

Si no la guardaste puedes consultarla en:

```bash
cat /etc/bandit_pass/bandit16
```

Para este nivel haremos un escaneo de puertos, será en en rango de 31000 a 32000

```bash
 nmap -sV localhost -p 31000-32000
```

El resultado del escaneo de puertos nos arrojó que el puerto más probable sería el 31790 potque maneja SSL/Unknown quiere decir que aparte de SSL maneja otro servicio y esto nos hace pensar que es el adecuado.

Para enviar la contraseña usando ssl tenemos que poner el siguiente comando y **pegar la contraseña para acceder a este nivel**:

```bash
openssl s_client -quiet -connect localhost:31790
```

**Copiar la llave privada.**

Nos dirijiremos a el directorio /tmp.

Para poder trabajar y crear archivos necesitamos un directorio temporal.

```bash
cd /tmp | mktemp -d
```

Con el comando anterior nos devuelve una salida con el directorio temporal creado, ahora tenemos que cambiar al nuevo directorio creado

```bash
cd /tmp/(DirectorioTemporalGenerado)
```

Vamos a crear un archivo de llave privada.

```bash
vim id_rsa
```

Ahora debemos de usar el editor vim, siguiendo estos pasos:

- esc
  
  - i 

- ctrl+v 

- esc 
  
  - :wq

Cambiaremos los permisos de la llave que acabamos de crear.

```bash
chmod 400 id_rsa
```

Usaremos la siguiente instrucción para acceder al siguiente nivel.

Este comando utiliza la llave que acabamos de crear .

```bash
 ssh -i id_rsa bandit17@localhost -p 2220
```

<hr>
<br>

## Nivel 17

Vamos a comparar los documentos y veremos cuales son las lineas que cambian entre uno y otro

```bash
diff passwords.old passwords.new
```

Las lineas de salida que tenemos en este comando se mostraran en el mismo orden en el que pusimos los archivos por lo que *la segunda linea es nuestra contraseña*

Ahora copia la contraseña para acceder al siguiente nivel.
<hr>
<br>

```admonish tip title='_Felicidades !!!!!!!_'
Superaste una etapa _desafiante_ <span style="color: hotpink">vamos por más! 🔥</span>
```

---

## Nivel 18 🚪🔐

En este nivel, **el archivo `readme` está vacío**, pero hay una trampa: ¡el archivo está oculto!

🔍 **¿Qué pasa?** Al iniciar sesión, el sistema **te desconecta inmediatamente**.

### 🧠 ¿Cómo lo resolvemos?

Vamos a usar el comando `ssh` con una opción extra para que **ejecute un comando directamente**, en lugar de abrir una shell interactiva.

```bash
ssh bandit18@localhost -p 2220 "cat readme"
```

📋 La contraseña para el siguiente nivel aparecerá como salida del comando.

---

## Nivel 19 🕵️‍♂️🧱

Aquí el sistema **mata automáticamente cualquier shell interactiva** que no sea del propio usuario.

🔑 Entonces, debemos "engañar" al sistema para que **piense que somos `bandit18`** mientras ejecutamos el siguiente comando.

### 🎩 Usamos `ssh` con una combinación especial:

```bash
ssh -p 2220 -i ./id_rsa bandit18@localhost "cat readme"
```

O también puedes usar este truco con `setuid`:

```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

💡 Aquí `bandit20-do` es un ejecutable especial con privilegios del siguiente usuario.

---

## Nivel 20 🧬🔗

Ahora necesitamos **crear un script personalizado** que será ejecutado por el programa `suconnect`.

🎯 Este script debe **escribir la contraseña en un archivo accesible para nosotros**.

### 🧪 Pasos:

1. Crear un archivo temporal:

```bash
cd /tmp
mkdir scriptlab
cd scriptlab
```

2. Crear el archivo `script.sh`:

```bash
vim script.sh
```

Contenido del archivo:

```bash
#!/bin/bash
cat /etc/bandit_pass/bandit20 > /tmp/password20.txt
```

3. Dar permisos de ejecución:

```bash
chmod +x script.sh
```

4. Ejecutar el programa con el script:

```bash
./suconnect 20 script.sh
```

5. Leer el archivo de salida:

```bash
cat /tmp/password20.txt
```

🎉 ¡Y listo! Tienes la contraseña del nivel 20.

---

