# 🌐 Kubernetes — Service & Ingress

## 🧩 1️⃣ Cos’è un **Service**?

👉 Un **Service** in Kubernetes fornisce un **IP statico (permanente)** 🔢 ai Pod.

* 🔗 Esempio pratico:

  * La tua **app** avrà un suo **Service dedicato**.
  * Il tuo **database** avrà un altro Service dedicato.

✅ **Punto chiave:**
Il **Service** ha un ciclo di vita **separato** dal Pod.
👉 Quindi:

* Se un Pod muore o viene ricreato, **l’IP del Service resta invariato**.
* Non devi aggiornare endpoint o configurazioni ogni volta.

---

## 🌍 2️⃣ Tipi di Service: **External vs Internal**

✨ **External Service**

* 📡 Serve per **esporre l’applicazione** verso l’esterno.
* Permette di ricevere richieste da **fonti esterne** (browser, utenti).

🔒 **Internal Service**

* Protegge risorse interne come il **database**.
* 🚫 Impedisce l’accesso diretto dall’esterno.
* Funziona solo **all’interno del cluster**.

---

## 🌐 3️⃣ Il problema: URL di base 🧩

Quando usi un **External Service** senza configurazioni extra:

* L’URL ha un formato **poco user-friendly**:
  `http://<Node-IP>:<Port>`
* 👉 Buono per **test veloci**, ma non per un’app **in produzione**:

  * Niente HTTPS
  * Niente dominio leggibile

---

## 🚦 4️⃣ Soluzione: **Ingress**

🔀 **Ingress** è un altro componente chiave di Kubernetes:

* 📥 Riceve le richieste esterne.
* 🔗 Fa da **proxy intelligente**:

  * Smista le richieste ai **Services** corretti.
  * Applica regole di routing.
  * Gestisce certificati SSL/TLS per HTTPS.

✅ Così puoi avere:

* 🌍 Un **URL pulito** tipo `https://myapp.com`
* 🔒 Connessione sicura

**Flusso:**
`Utente esterno → Ingress → Service → Pod`

---

## ✅ 5️⃣ Riepilogo

📌 Con Service & Ingress puoi:

* Mantenere **endpoint stabili** anche se i Pod cambiano.
* Esporre solo quello che serve (app esterna sì, DB no).
* Offrire un **accesso sicuro e professionale** con dominio e HTTPS.

---

## 🚀 6️⃣ E ora?

✨ Finora hai visto:

* 1 server (Node)
* 2 container (Pod)
* Services per stabilità di rete
* Ingress per ingresso sicuro da Internet

Ma i **veri superpoteri** di Kubernetes (scalabilità automatica, bilanciamento carico, auto-riparazione) ✨ arriveranno man mano nei prossimi step!

