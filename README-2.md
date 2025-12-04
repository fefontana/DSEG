DSEG Font Family
====

## Como convertir las fuentes de ttf a woff

ChatGPT no puede **suministrar directamente** los archivos `.woff2` o `.woff` de la fuente **DSEG7**, si estos están bajo una licencia que no permite su distribución sin permiso explícito.

Pero aca hay una guia para conseguirlos legalmente e instalarlo correctamente:

---

## 💡 Cómo descargar DSEG7 legalmente

1. Ve al repositorio oficial de DSEG:
   [GitHub – DSEG](https://github.com/keshikan/DSEG)

2. Busca la carpeta `DSEG7` (o la variante “7-Segment”) y bajá los archivos `.ttf` desde ahí.

3. Convertí el `.ttf` a `.woff2` y `.woff` si no vienen ya listos. Hay herramientas en línea gratuitas o podés usar `fonttools`:

   ```bash
   pip install fonttools
   ttx -o DSEG7Classic-Regular.woff2 -f woff2 DSEG7Classic-Regular.ttf
   ttx -o DSEG7Classic-Regular.woff -f woff DSEG7Classic-Regular.ttf
   ```

---

Perfecto: **un archivo `.sfd` es la fuente editable de FontForge**.
Con ese archivo se puede generar fácilmente:

* **.woff2** (para web moderno)
* **.woff** (compatibilidad)
* **.ttf** (truetype)
* **.otf** (opentype)

Pero necesito que **subas el archivo `DSEG7Classic-Regular.sfd` aquí**, así puedo convertirlo dentro del entorno y generarte:

```
/assets/fonts/DSEG7/DSEG7Classic-Regular.woff2
/assets/fonts/DSEG7/DSEG7Classic-Regular.woff
```

📌 **Subilo ahora mismo y lo convierto automáticamente.**


Si ya tenés **DSEG7Classic-Regular.sfd**, podés convertirlo a **.woff2** y **.woff** usando **FontForge desde la terminal**.

Acá tenés los comandos exactos 👇

---

# ✅ **1. Instalar FontForge (si no lo tenés)**

### Ubuntu / Debian

```bash
sudo apt update
sudo apt install fontforge
```

### Arch

```bash
sudo pacman -S fontforge
```

### macOS (Homebrew)

```bash
brew install fontforge
```

---

# ✅ **2. Convertir `.sfd` → `.ttf`**

```bash
fontforge -lang=ff -c 'Open($1); Generate($2)' DSEG7Classic-Regular.sfd DSEG7Classic-Regular.ttf
```

---

# ✅ **3. Convertir `.ttf` → `.woff`**

```bash
fontforge -lang=ff -c 'Open($1); Generate($2)' DSEG7Classic-Regular.ttf DSEG7Classic-Regular.woff
```

---

# ✅ **4. Convertir `.ttf` → `.woff2`**

FontForge no exporta woff2 directo, pero podés usar **woff2-tools**:

### Instalar woff2

Ubuntu:

```bash
sudo apt install woff2
```

macOS:

```bash
brew install woff2
```

### Convertir

```bash
woff2_compress DSEG7Classic-Regular.ttf
```

Esto genera:

```
DSEG7Classic-Regular.woff2
```

---

# 📁 Resultado final esperado

En tu carpeta vas a tener:

```
DSEG7Classic-Regular.sfd
DSEG7Classic-Regular.ttf
DSEG7Classic-Regular.woff
DSEG7Classic-Regular.woff2
```

---

EJEMPLO DE COMANDOS



  522  fontforge -lang=ff -c 'Open($1); Generate($2)' DSEG14Modern-Regular.sfd DSEG14Modern-Regular.ttf
  523  fontforge -lang=ff -c 'Open($1); Generate($2)' DSEG14Modern-Regular.ttf DSEG14Modern-Regular.woff
  524  woff2_compress DSEG14Modern-Regular.ttf
  
  
LUEGO REFERENCIAR ASI:

@font-face {
    font-family: 'DSEG7';
    src: url('../assets/fonts/DSEG7/DSEG7Classic-Regular.woff2') format('woff2'),
          url('../assets/fonts/DSEG7/DSEG7Classic-Regular.woff') format('woff');
    font-weight: normal;
    font-style: normal;
}

@font-face {
    font-family: 'DSEG14';
    src: url('../assets/fonts/DSEG14/DSEG14Classic-Regular.woff2') format('woff2'),
        url('../assets/fonts/DSEG14/DSEG14Classic-Regular.woff') format('woff');
    font-weight: normal;
    font-style: normal;
}

@font-face {
    font-family: 'DSEG14Modern';
    src: url('../assets/fonts/DSEG14Modern/DSEG14Modern-Regular.woff2') format('woff2'),
        url('../assets/fonts/DSEG14Modern/DSEG14Modern-Regular.woff') format('woff');
    font-weight: normal;
    font-style: normal;
}

.dseg7{
  font-family: 'DSEG7', monospace;
  font-size: 1.2rem;
  letter-spacing: 2px;
}
.dseg14{
  font-family: 'DSEG14', monospace;
  letter-spacing: 2px;
}
.dseg14Modern{
  font-family: 'DSEG14Modern', monospace;
  letter-spacing: 2px;
}

EN HTML:

        <a href="index.html" class="logo m-0"><span class="logo-bit dseg7" style="font-style: italic;">b<span class="i-fix">i</span>t</span><span class="text-primary-logo">SYSTEM</span><span class="text-primary">.</span>dev</a>



