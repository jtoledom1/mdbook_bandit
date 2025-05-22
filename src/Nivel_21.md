# Nivel 20-25
---

## Nivel 21 🧾📡

🧠 En este nivel tenemos un programa que **escucha conexiones en un puerto específico**. Nuestra misión es **enviarle un mensaje especial**.

### 🔧 Pasos:

1. Ve al directorio donde está el ejecutable:

```bash
cd /etc/bandit_pass
```

2. Corre el binario con `nc` (netcat):

```bash
./suconnect 22
```

Te dirá que **espera una clave específica**. Esa clave está en el archivo:

```bash
cat /etc/bandit_pass/bandit21
```

📤 Después, debes conectar al puerto correcto y **enviar la contraseña**.

---

## Nivel 22 🌐🔎

Aquí necesitamos **conectarnos a un servidor HTTP** que solo acepta conexiones desde `localhost`.

🔧 Solución: usamos **curl** para hacer la solicitud desde dentro del servidor:

```bash
curl http://localhost:80
```

🧠 Si ves que responde con HTML, perfecto. Ahora, busca el endpoint secreto:

```bash
curl http://localhost:80/index.html
```

Inspecciona el contenido y sigue los enlaces hasta encontrar la contraseña. Usa comandos como:

```bash
curl -s http://localhost:80/secret-directory/
```

---

## Nivel 23 🧩🔒

🎯 El servidor ahora espera una **cookie especial**. Si no la mandas, no da acceso.

### 🍪 ¿Cómo hacerlo?

1. Accede primero para ver qué respuesta devuelve:

```bash
curl -i http://localhost:80
```

2. Luego usa la cookie que te pide:

```bash
curl --cookie "foo=bar" http://localhost:80
```

Reemplaza `"foo=bar"` por lo que el servidor espera. Con un poco de prueba y error (o viendo pistas en el HTML), llegas a la contraseña.

---

## Nivel 24 ⚙️🔁

Este reto nos da un binario llamado `bandit24` que se comporta como un **servidor** esperando conexiones.

👣 Lo que tienes que hacer es:

1. Crear un script que **actúe como cliente** y mande una contraseña:

```bash
#!/bin/bash
echo "contraseña_de_bandit23"
```

2. Luego conecta usando netcat:

```bash
./bandit24 &  # Esto lo ejecuta en segundo plano
nc localhost 30002 < script.sh
```

💥 Te devuelve la contraseña si todo va bien.

---

## Nivel 25 🔂🔐

Este es **el nivel final del reto Bandit** 🎉

🔍 El binario `bandit25` **se conecta a un servidor externo remoto**.

🧠 ¿El truco? Simular **ese servidor externo** en tu máquina y hacer que el programa se conecte **a ti** en vez del original.

### ⚙️ Pasos:

1. Crear un archivo script que imprima la contraseña:

```bash
echo "contraseña_de_bandit24" > mensaje.txt
```

2. Levanta un servidor falso:

```bash
nc -l -p 30001 < mensaje.txt
```

3. Luego ejecuta el binario para que **se conecte a ese puerto**:

```bash
./bandit25 localhost 30001
```

🚀 Y con eso deberías obtener la contraseña del último nivel.

---

### 🎉 ¡Felicidades hacker! 🧠💻

Si llegaste hasta aquí, dominaste una tonelada de herramientas útiles de Linux y pentesting básico. Prepárate para retos aún más complejos (como Narnia, Leviathan o Krypton 🔐).
