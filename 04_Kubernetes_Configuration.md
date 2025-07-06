# ⚙️ Kubernetes Configuration

## 🗂️ 1️⃣ Come funziona la configurazione in Kubernetes?

💡 In Kubernetes **tutte le configurazioni** passano attraverso il **Master Node**, grazie al processo **API Server**:

* ✅ L’**API Server** è **l’unico punto di ingresso** per interagire col cluster.
* Client Kubernetes:

  * 📺 UI → es. **Kubernetes Dashboard**
  * 📜 API → script, `curl`
  * 🖥️ CLI → `kubectl`

Tutti parlano all’**API Server** inviando **richieste di configurazione**.

---

## 📑 2️⃣ Formato della configurazione

📄 Le configurazioni Kubernetes sono:

* 🧾 In formato **YAML** (o JSON).
* 👉 Il formato più comune è **YAML** (`.yaml` o `.yml`).

---

## 📋 3️⃣ Esempio pratico: Deployment (il quale è il blueprint del progetto per la creazione di pods)

✨ Esempio di file YAML:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec: # specification part
  replicas: 2  # crea due replicas pds
  template:
    spec:
      containers:
      - name: my-app
        image: my-image
        env:
        - name: ENV_VAR
          value: "value"
        ports:
        - containerPort: 80
```

👉 Con questo file:

* Crei un **Deployment**.
* Dichiari di voler **2 repliche** di `my-app`.
* Ciascun pod replica ha un containaer basato sulla nostra immagine in esecuzione al suo interno.
* Inoltre Specifica:

  * Immagine container.
  * Variabili d’ambiente.
  * Porte esposte.

  All'interno di ciascun replicas pod

---

## 🔁 4️⃣ Configurazione **dichiarativa**

📌 Kubernetes usa una logica **dichiarativa**:

* Dichiarazione: “**Voglio questo stato desiderato!**”
* Esempio: “Voglio 2 repliche.”
* Kubernetes confronta:

  * Stato **desiderato** (spec).
  * Stato **attuale** (status).

Se non coincidono:

* Il **Controller Manager** interviene.
* Esempio: Se 1 Pod muore → Kubernetes **crea un nuovo Pod** per tornare a 2.

✅ Questo è il principio di **self-healing**!

---

## 🧩 5️⃣ Struttura di un file YAML

Ogni file di configurazione Kubernetes ha **3 parti** fondamentali:

| Parte                        | Descrizione                                              |
| ---------------------------- | -------------------------------------------------------- |
| **1️⃣ Metadata**             | Info generali: nome, namespace, etichette                |
| **2️⃣ Specification (spec)** | Dettagli: configurazione specifica del componente        |
| **3️⃣ Status**               | Stato attuale (aggiunto da Kubernetes **in automatico**) |

✨ **Esempio:**

* `metadata:` → Nome del Deployment o Service.
* `spec:` → Replica, immagine, porte, regole.
* `status:` → Generato da Kubernetes. Tiene traccia dello stato reale.

---

## 🧠 6️⃣ Da dove arriva lo stato? → `etcd`

🔍 Lo **stato** (`status`) dei componenti è salvato in **etcd**:

* 📌 È il “**cervello**” del cluster.
* 🧩 Contiene tutta la configurazione + stato aggiornato.
* Kubernetes lo usa per confrontare e garantire coerenza.

---

## ⚠️ 7️⃣ YAML: attenzione all’indentazione!

✔️ **YAML è semplice**, ma:

* È **molto rigoroso** con spazi e indentazioni.
* Un errore di indentazione = file **non valido**.

---

## 🗂️ 8️⃣ Best practice: dove salvare i file YAML?

💡 I file YAML di configurazione:

* 📂 Vanno salvati **insieme al codice sorgente** dell’applicazione.
* Oppure in un **repository dedicato** (`git`).
* 👉 Questo segue la filosofia **Infrastructure as Code** (IaC):

  * Tutta l’infrastruttura è **versionata**.
  * Facile da condividere e mantenere.

---

## ✅ 9️⃣ Riassunto

📌 **Flusso completo**:
1️⃣ Scrivi file YAML.
2️⃣ Applichi (`kubectl apply -f`).
3️⃣ L’API Server riceve la richiesta.
4️⃣ Kubernetes **confronta stato desiderato e attuale**.
5️⃣ Se serve, esegue azioni (crea Pod, rimuove, aggiorna).
6️⃣ Stato attuale aggiornato in `etcd`.

✨ Questo rende Kubernetes **resiliente**, **scalabile** e **autosufficiente** nel mantenere lo stato!
