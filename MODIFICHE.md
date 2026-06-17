# REGISTRO MODIFICHE — QMS Temperature
> File: `index.html` | Ultimo aggiornamento: 2026-04-03

---

## Modifiche apportate

### 1. Aggiunta libreria Firebase Auth (mancante)
Il file includeva solo `firebase-app-compat.js` e `firebase-firestore-compat.js`. Aggiunto:
```html
<script src="https://www.gstatic.com/firebasejs/10.12.2/firebase-auth-compat.js"></script>
```

---

### 2. Autenticazione Firebase
**Prima:** nessuna autenticazione — accesso a Firestore senza token, incompatibile con le nuove Security Rules.
**Dopo:** `firebase.auth().signInWithEmailAndPassword('farmacia.ascona@gmail.com', ...)`

---

### 3. Sistema di controllo dispositivi
Aggiunto overlay di autorizzazione all'avvio della webapp.

**Comportamento:**
- Dispositivo non riconosciuto → schermata con campo codice admin
- Codice corretto → assegna nome → dispositivo registrato su Firestore (`dispositivi`)
- Accessi successivi → controllo automatico, accesso diretto
- Dispositivo revocato dall'admin → overlay riappare

**Codice admin:** verificato tramite hash SHA-256 hardcoded nel file.

---

## Stato sicurezza attuale

| Controllo | Stato |
|-----------|-------|
| Libreria Firebase Auth aggiunta | ✅ |
| Login con email/password dedicata | ✅ |
| Firestore Security Rules aggiornate | ✅ |
| Controllo dispositivi operativo | ✅ |
| Codice admin hardcoded come hash SHA-256 | ✅ |
