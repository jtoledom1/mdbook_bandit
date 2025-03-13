# Nivel 16

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
