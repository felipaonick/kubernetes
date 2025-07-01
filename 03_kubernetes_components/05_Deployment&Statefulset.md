# 🚀 Deployment & StatefulSet in Kubernetes

## ⚡ 1️⃣ Il problema: downtime

💡 Con la configurazione vista finora:

* Utente → Accede all’app tramite **browser** 🌐.
* Se il **Pod dell’app** si blocca o si riavvia → 👉 L’app **diventa irraggiungibile**! ❌

⏳ Anche un semplice **update** (es. nuova immagine container) causerebbe **downtime** → Inaccettabile in produzione!

---

## 🔗 2️⃣ Replica & Alta disponibilità

✨ **Kubernetes** risolve questo problema con la **replica**:

* Non fai girare **un solo Pod**, ma **più copie identiche** distribuite su **nodi diversi**.
* Se un Pod si blocca, un altro prende il carico → **Zero downtime** per l’utente! ✔️

---

## 🧩 3️⃣ Service = Load Balancer

Ricorda:

* ✅ Un **Service** non è solo un IP statico + DNS → È anche un **Load Balancer**!
* 📡 Riceve le richieste e le **distribuisce** sui Pod disponibili → Sceglie quello meno occupato.

---

## 🗂️ 4️⃣ Deployment

🚀 In Kubernetes non crei manualmente **n Pod**.
👉 Crei un **Deployment**, che è:

* Un **blueprint** (modello) per i tuoi Pod.
* 📑 Definisci:

  * **Quanti Pod** desideri (`replicas`) per un certo pod.
  * Politiche di **scaling** (aumentare o diminuire Pod).
  * Strategie di aggiornamento (rolling update).

**In pratica:**
Lavori quasi sempre con **Deployment**, non con Pod singoli!

---

## 🧵 5️⃣ Abbreviazione delle astrazioni

📌 Schema di astrazione:

* **Container** = unità base.
* **Pod** = astrazione sul Container.
* **Deployment** = astrazione sul Pod.

✨ Il Deployment semplifica:

* Replica.
* Aggiornamento.
* Autoscaling.

---

## 🗃️ 6️⃣ E i database? Serve **StatefulSet**

📌 Problema:

* L’app è **stateless**, quindi facile da replicare.
* Ma il **database** è **stateful**:

  * Ha uno **stato persistente** (dati!).
  * Replica = più Pod DB = tutti devono accedere allo **stesso storage condiviso**.

👉 **Serve coordinamento** per:

* Evitare conflitti di lettura/scrittura.
* Mantenere **consistenza** dei dati.

✅ Soluzione Kubernetes: **StatefulSet**

* 🔗 Replica Pod **stateful** in modo ordinato.
* 📌 Coordina accesso a storage condiviso.
* Garantisce ordini di start, shutdown e naming.

---

## 🧩 7️⃣ Deployment vs StatefulSet

| **Aspetto**       | **Deployment**    | **StatefulSet**                   |
| ----------------- | ----------------- | --------------------------------- |
| Tipo di app       | **Stateless**     | **Stateful**                      |
| Replica           | Facile, scalabile | Replica con gestione stato        |
| Uso tipico        | App web, API      | DB: MySQL, MongoDB, Elasticsearch |
| Ordine avvio/stop | Non garantito     | Garantito                         |

---

## 🔒 8️⃣ Nota pratica

⚠️ **Deployare DB dentro Kubernetes?**

* Può essere complicato!
* StatefulSet funziona, ma serve attenzione a:

  * Replica dei dati.
  * Backup.
  * Consistenza.

👉 **Best practice comune:**

* Tenere **DB esterni** (managed DB, on-prem) fuori dal cluster.
* Usare Kubernetes solo per applicazioni **stateless** → Replica facile.

---

## ✅ 9️⃣ Risultato: Alta disponibilità

Con:

* Più **repliche dell’app** (Deployment).
* Più **repliche del DB** (StatefulSet o DB esterno).
* **Load balancing** automatico (Service).

👉 Se un nodo si guasta:

* L’altro **continua a servire utenti**.
* ❌ Niente downtime!

---

## 📌 10️⃣ Ricapitolone finale

Abbiamo visto:

* 🧩 **Pod & Service** → Comunicazione e IP statico.
* 🌐 **Ingress** → Traffico da esterno a dentro il cluster.
* 🗂️ **ConfigMap & Secret** → Config esterna e dati sensibili.
* 💾 **Volume** → Persistenza dati.
* 🚀 **Deployment & StatefulSet** → Replica, scalabilità, gestione stateless/stateful.

💪 Solo con questi **core components** puoi già costruire cluster **robusti e pronti per produzione**.

---

## 🎉 Bonus: Backup smart

✨ Strumento citato: **Kasten K10**

* 🔄 Piattaforma di **data management** per Kubernetes.
* Automatizza **backup** e **restore** → Solleva l’admin da compiti ripetitivi.
* UI semplice + logica intelligente → Facilita la gestione.
