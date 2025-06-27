# 📚 Kubernetes Crash Course — Intro & Course Overview

---

## 🗺️ Cosa imparerai?

Ecco una panoramica dei temi principali del corso:

1️⃣ **Cos'è Kubernetes?**

* Perché è nato?
* Perché è diventato così popolare?

2️⃣ **Architettura di Kubernetes 🏗️**

* Vedrai come funziona Kubernetes “dietro le quinte”.

3️⃣ **Componenti principali 🔧**

* Scoprirai gli elementi essenziali per lavorare in modo efficace con Kubernetes.

4️⃣ **Demo pratica 👩‍💻**

* Farai un **progetto pratico** per ottenere la tua prima esperienza reale con Kubernetes.

---

## 🤔 Perché questo corso è importante?

✨ Kubernetes è una tecnologia **molto popolare**, ma anche **complessa**.
👉 Questo crash course ti darà una **prima esperienza pratica** per iniziare con il piede giusto.

---

## 🎓 Vuoi diventare un amministratore Kubernetes?

Se alla fine del video deciderai di approfondire:

* 🚀 Ho creato un corso completo per diventare **Kubernetes Administrator**.
* 📚 Imparerai a **creare, configurare e gestire cluster Kubernetes da zero**.
* ✅ Il corso ti aiuterà anche a superare l’**esame CKA (Certified Kubernetes Administrator)** della Linux Foundation!

---

## ⚡ Iniziamo subito!

Abbiamo molto da coprire in questo video, quindi **iniziamo subito!**
📌 Prossimo passo: **Definizione di Kubernetes**
💡 *Spoiler*: Kubernetes è un **progetto open source**.

# 📦 What is Kubernetes?

## 🌐 1️⃣ Cos'è Kubernetes?

🗂️ **Kubernetes** è un **framework di orchestrazione dei container**, sviluppato inizialmente da **Google**.
👉 La sua funzione principale è **gestire container**, che siano container **Docker** o di altre tecnologie.

---

## 🧩 2️⃣ Perché usare Kubernetes?

Oggi molte applicazioni moderne sono costituite da **centinaia o migliaia di container** 🚢. Kubernetes ti aiuta a:

* 🖥️ Gestire queste applicazioni in diversi ambienti:

  * Macchine fisiche
  * Macchine virtuali
  * Cloud ☁️
  * Ambienti **ibridi**

---

## ⚙️ 3️⃣ Quali problemi risolve Kubernetes?

🔍 Vediamo perché è nato Kubernetes, seguendo un ordine cronologico:

* 📈 **Crescita dei Microservizi**
  👉 Lo sviluppo dei **microservizi** ha aumentato l’uso dei container, perché i container sono perfetti per ospitare piccole applicazioni indipendenti.

* 🧮 **Aumento dei container**
  👉 Le app moderne sono spesso formate da **centinaia o migliaia di container**, distribuiti su più ambienti.

* 🗂️ **Gestione manuale impossibile**
  👉 Gestire questi container con **script o strumenti artigianali** è molto complesso, a volte impossibile.

🛠️ **Soluzione:** nasce la necessità di strumenti di **orchestrazione dei container**, come Kubernetes.

---

## 🚦 4️⃣ Funzionalità chiave di Kubernetes

💡 Cosa garantisce un tool di orchestrazione come Kubernetes? Ecco le **3 funzionalità principali**:

1️⃣ **High Availability (Alta Disponibilità) 🔄**

* Significa che l’applicazione non ha **interruzioni di servizio**.
* Gli utenti possono accedere sempre all’app.

2️⃣ **Scalability (Scalabilità) 📈**

* Puoi **scalare l’applicazione velocemente** quando il carico aumenta (es. più utenti).
* Allo stesso modo, puoi **ridurre le risorse** quando il carico diminuisce.
* 📊 Massima flessibilità.

3️⃣ **Disaster Recovery (Recupero in caso di disastro) 🔒**

* Se l’infrastruttura ha problemi (es. perdita di dati, server guasti), deve esserci un **backup automatico**.
* Kubernetes permette di **ripristinare l’applicazione all’ultimo stato funzionante** senza perdita di dati.

---

✅ Queste funzionalità rendono Kubernetes una **soluzione robusta** per la gestione di **applicazioni containerizzate** su larga scala.

---

## 📌 Prossimo step: **Architettura di base di Kubernetes**

✨ Ora vedremo **come è fatta l’architettura di Kubernetes** e come funziona “dietro le quinte”.


