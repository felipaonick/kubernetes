# ⚙️ Kubernetes Components — Node & Pod

## 📌 1️⃣ Introduzione pratica

👉 In questa parte, impariamo i **principali componenti di Kubernetes** su cui lavorano **amministratori** e **utenti** ogni giorno.

💡 Per semplificare, vedremo un **caso d’uso reale**:
➡️ Una **web application** 🕸️ con un **database** 🗄️
➡️ Analizzeremo **passo passo** come ogni componente aiuta a **deployare** questa architettura.

---

## 🖥️ 2️⃣ Cos'è un **Node**?

🔹 Un **Node** (nodo) è un **server fisico o virtuale** nel cluster Kubernetes.

* Sui nodi girano i **container** delle tue applicazioni.
* Kubernetes considera **qualsiasi server** (fisico, VM, cloud) come un **Node**.

---

## 📦 3️⃣ Cos'è un **Pod**?

✨ Il **Pod** è la **unità più piccola** di Kubernetes.
👉 È un livello di **astrazione sopra un container**.

**Dettagli chiave:**

* Se conosci Docker, pensa al Pod come a un **wrapper sopra il container**.
* 🎯 Il Pod crea un **ambiente di esecuzione isolato** per uno o più container.
* 🔄 Motivo: Kubernetes vuole **astrarre** la tecnologia del runtime dei container (es. Docker) → così puoi **sostituirla** o aggiornarla senza problemi.
* 📌 Come utente interagisci solo con i **Pod**, non con Docker direttamente.

---

## 🧩 4️⃣ Esempio pratico

📌 Immagina:

* Hai un **Pod dell’applicazione** → esegue la tua web app.
* Hai un **Pod del database** → esegue il database.

👉 Di solito **un Pod = un container**.
🛑 Puoi avere **più container** nello stesso Pod **solo in casi particolari**, ad esempio:

* Un **container principale** (main app).
* Un **helper container** (sidecar) per log, proxy, backup, ecc.

---

## 🌐 5️⃣ Rete tra Pod

📡 Kubernetes fornisce **una Virtual Network di default**:

* Ogni **Pod riceve un indirizzo IP interno unico**.
* 📶 Non è il container ad avere l’IP, ma il **Pod**.
* I Pod possono comunicare tra loro usando questi **IP interni**.

➡️ Esempio:

* La web app comunica col database usando l’**IP del Pod database**.

---

## ⚠️ 6️⃣ Pod = Effimeri

🔄 **Attenzione!** I Pod sono **effimeri**:

* Possono morire facilmente:

  * Crash dell’applicazione.
  * Problemi di risorse sul Node.
* Se un Pod muore, Kubernetes ne crea uno nuovo **automaticamente**.
* 👉 **Nuovo Pod = Nuovo IP** ❗

---

## 🔗 7️⃣ Problema → Soluzione

💥 Se usi l’**IP del Pod** per connetterti al database:

* Ad ogni restart → nuovo IP → devi aggiornare le connessioni.
* 🔄 È **impraticabile** gestirlo manualmente.

✅ **Soluzione Kubernetes:** il **Service**

* Un componente che risolve il problema degli IP **variabili**.
* 📌 Fornisce un **endpoint fisso** per accedere ai Pod, anche se questi vengono ricreati.
