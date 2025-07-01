# 🗂️ ConfigMap & Secret in Kubernetes

## 🔗 1️⃣ Ripasso: comunicazione tra Pod

👉 I **Pod** comunicano tra loro grazie ai **Services**.

* Esempio: la tua app usa un **endpoint** per parlare con il database:
  `mongo-db-service` che segue `url:porta/endpoint` proprio come in FastAPI

📌 Di solito questi **endpoint** (es. URL, nomi di servizi) vengono:

* Di solito questi endpoint si configurano nel file delle proprietà della applicazione che di solito si trova all'interno dell'immagine creata dall'applicazione
* Salvati in un **file di configurazione** dell’app.
* Oppure come **variabili d’ambiente**.

---

## ⚠️ 2️⃣ Il problema delle configurazioni statiche

🤔 Se il nome dell’**endpoint del servizio cambia** (es. `mongodb` → `mongodb-prod`):

* Devi **modificare tale URL/endpoint nel file di configurazione** nell’app.
* 👉 Poi **ricompilare l’immagine Docker** (re-build), fare il **push nel repository**, **ricreare il Pod**… 🔄
* Troppo lavoro per un cambio così piccolo, come la modifica del nome di un endpoint! 😅

---

## ✅ 3️⃣ La soluzione: **ConfigMap**

🗂️ **ConfigMap** è un componente Kubernetes per:

* 🧩Gestisce **configurazioni esterne** della nostra applicazione.
* 🗂️ Contenere dati come URL, nomi di servizi (endpoints), variabili di configurazione.

✨ Vantaggi:

* Si **collega al Pod** → Il Pod legge i dati dal ConfigMap.
* Se l’endpoint cambia, basta **modificare il ConfigMap**:

  * 🚫 Nessuna nuova build.
  * 🚫 Nessun push di immagini.
  * 🚫 Nessun deploy pesante.

---

## 🔒 4️⃣ Configurazioni sensibili: **Secret**

🔑 Oltre agli endpoint, spesso, come parte della configurazione esterna dell'aplicazione, hai anche **credenziali sensibili**:

* Username e password del DB.
* API keys.
* Certificati.

Che anch'esse possono cambiare nel processo di deployment dell'applicazione

🛑 Non metterli in chiaro in un **ConfigMap**!

✅ Soluzione: **Secret**

* Simile al ConfigMap ma per **dati segreti**.
* I dati sono codificati in **Base64**.
* 👉 Di default **non sono cifrati** → Devi usare tool esterni (cloud provider o terze parti) per **crittografare i Secret**.

---

## 🔐 5️⃣ Best Practice

✨ **ConfigMap**

* Per configurazioni **non sensibili**.

  * Esempi: URL, nomi di servizio (endpoints), parametri di ambiente comuni.

✨ **Secret**

* Per dati **sensibili**:

  * Password.
  * Certificati.
  * Token di accesso.

---

## ⚙️ 6️⃣ Come si usano?

📌 Puoi collegare **ConfigMap** o **Secret** ai Pod:

* Come **variabili d’ambiente**.
* Come **file di proprietà** montati come volume.

Il Pod può così **leggere i dati** quando serve.

---

## 🚀 7️⃣ Ricapitolando

* **ConfigMap** 📂: Configurazioni generiche → Facili da aggiornare.
* **Secret** 🔐: Dati sensibili → Da proteggere con crittografia.
* Entrambi:

  * ✅ Separano configurazioni dal codice.
  * ✅ Riducono rebuild e downtime.
  * ✅ Rendono il deploy più flessibile e sicuro.

