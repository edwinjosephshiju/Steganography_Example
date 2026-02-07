
# 🐱 Hidden Cat Photo – Steganography Demo (Windows · Linux · Termux)

> A harmless-looking cat photo that secretly contains hidden files.

---

## 🧠 Core Concept (ASCII View)

### 1️⃣ Normal Image File
```
[ JPG HEADER ][ IMAGE DATA ][ EOF ]
```

### 2️⃣ ZIP File
```
[ ZIP HEADER ][ FILE DATA ][ ZIP INDEX ]
```

### 3️⃣ After Hiding (Final File)
```
[ JPG HEADER ][ IMAGE DATA ][ EOF ][ ZIP HEADER ][ FILE DATA ][ ZIP INDEX ]
                     ↑
          Image viewers STOP here
```

➡️ Image viewers ignore everything after EOF  
➡️ ZIP tools scan the entire file and find ZIP headers

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
 │               │        │ Tool           │
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

```
cat.jpg      : [ JPG DATA ]
secret.zip   : [ ZIP DATA ]
--------------------------------
hidden_cat.jpg: [ JPG DATA ][ ZIP DATA ]
```

---

# Linux / Termux
```
cat cat.jpg secret.zip > hidden_cat.jpg
```

Same result. Different spell.

---

## 🧪 Extraction Flow

```
User downloads image
        |
        v
Double-click image ──► Looks normal
        |
        v
Open with ZIP tool
        |
        v
ZIP HEADER FOUND
        |
        v
Secret extracted 🎯
```

---

## 🛡️ Security Lesson (Why This Matters)

```
File Extension  ≠  File Truth
```

- Antivirus checks CONTENT
- Humans trust NAMES
- Attackers exploit that gap

---

## 🧠 Mental Model to Remember

```
A file is NOT:
"An image"
"A document"
"An archive"

A file IS:
"A stream of bytes with patterns"
```

Once you understand this, **half of cybersecurity suddenly makes sense.**

---

## 📜 License
MIT — learn responsibly.
