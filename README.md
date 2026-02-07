
# 🐱 Hidden Cat Photo – Steganography Demo (Windows · Linux · Termux)

![Cat JPG](cat.jpg)

> A harmless-looking cat photo that secretly contains hidden files.  
> Looks innocent. Behaves differently depending on *who* opens it.

---

# 🚀 Quick Start (Termux – One Command)

Copy‑paste **exactly one command** in Termux:

```bash
pkg update && pkg install git zip -y && git clone https://github.com/YOUR_USERNAME/hidden-cat-photo.git && cd hidden-cat-photo
```

---

## 🧠 Core Concept (ASCII View)

### 1️⃣ Normal Image File

[ JPG HEADER ][ IMAGE DATA ][ EOF ]


### 2️⃣ ZIP File

[ ZIP HEADER ][ FILE DATA ][ ZIP INDEX ]


### 3️⃣ After Hiding (Final File)

```
    [ JPG HEADER ][ IMAGE DATA ][ EOF ][ ZIP HEADER ][ FILE DATA ][ ZIP INDEX ]
                                         ↑
                               Image viewers STOP here
```
---
## 🔀 How Different Programs See the Same File

```
             ┌─────────────────────┐
             │  hidden_cat.jpg     │
             └─────────────────────┘
                     │
        ┌────────────┴─────────────┐
        │                          │
 ┌───────────────┐        ┌────────────────┐
 │ Image Viewer  │        │ ZIP / Archive  │
 │ Reads JPG     │        │ Scans for ZIP  │
 │ Stops at EOF  │        │ Ignores JPG    │
 └───────────────┘        └────────────────┘
        │                          │
   🐱 Cute Cat              📦 secret.txt
```

---

## 🪄 Command-Level View

# Windows
```
copy /b cat.jpg + secret.zip hidden_cat.jpg
```

---

# Linux / Termux
```
cat cat.jpg secret.zip > hidden_cat.jpg
```

---

## 📜 License
MIT — learn responsibly.
