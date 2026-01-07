# Daily Notes – TryHackMe



## 2026-01-06

**Room: Cybersecurity 101 - John the Ripper, The Basics**  
**Tema: #johntheripper #hash-cracking #wordlists #hash-formats**  

### 🧠 Aprendido
- Identificar tipos de hash con hash-id (verificar como lo llama John --format)
- Cracker hashes con Jhon
- Hash windows tipo NT

### 🛠️ Comando / concepto clave
- python3 hash-id.py
- john --list=formats | grep -iF "md5"
- john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt

### 🎯 Uso real
- Auditoría offline: detectar contraseñas débiles a partir de hashes filtrados.
- Elegir bien el `--format` y tirar de `rockyou` para validar riesgo rápido.

---

## 2026-01-07

**Room: Cybersecurity 101 - John the Ripper, The Basics**  
**Tema: Cracking /etc/shadow Hashes**  

### 🧠 Aprendido
- Cracking Linux Hashes
- mangling rules
- Single crack mode - Genero contraseñas probables a partir del nombre del usuario y sus datos
- custom rules

### 🛠️ Comando / concepto clave
- john local_shadow (autoidentifica el formato del hash y lo crackea, le podriamos pasar el formato)
- unshadow local_passwd local_shadow > unshadowed.txt
- john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt unshadowed.txt
- john --single --format=Raw-MD5 hash07.txt 
- john --wordlist=[path to wordlist] --rule=PoloPassword [path to file]

### 🎯 Uso real
- Comprobar impacto si se filtran `passwd` + `shadow` (qué cuentas caen).
- Probar patrones reales con `--single` y `--rules` (nombres, años, sufijos).
