# **🚀 Brain Meeting Report: Progetto Federscout 2.0**

Documento di Analisi e Ristrutturazione Architetturale  
Data: 01/01/2026  
Oggetto: Razionalizzazione contenuti "IdeeBe" e Setup Backend Spring Boot

## **1\. Analisi "IdeeBe" & Riorganizzazione UX/UI**

Il sito originale presenta una dispersione dei contenuti con troppe voci di menu separate per anno o micro-argomento. L'obiettivo è accorpare e semplificare, trasformando pagine statiche in flussi dinamici gestiti dal database.

Di seguito la nuova sitemap logica che integra le note del PDF e i nuovi raggruppamenti suggeriti quali Feder Letter, Convenzioni, News ed Eventi.

### **🟢 Nuova Struttura della Sitemap \- Frontend View**

#### **1\. HOME PAGE \- Hub Centrale**

*Struttura delineata in verde nel PDF*

* **Hero Section:** Video o Immagine emozionale di presentazione con Link al Canale YouTube Federscout.  
* **In Evidenza \- Dynamic:** Box scorrevole con le ultime 3 News o Eventi imminenti.  
* **Chi Siamo \- Preview:** Breve estratto con link alla sezione dedicata.  
* **Accesso Rapido:** Icone per Calendario Eventi e Documenti Recenti.

#### **2\. CHI SIAMO \- Il Cuore Istituzionale**

*Unificazione di: Storia, Elenco Associazioni, Comitato, Statuto*

* **La Nostra Storia:** Migrazione contenuto dalla sezione "breve storia della federscout".  
* **Struttura Organizzativa:**  
  * *Consiglio Federale:* Foto e ruoli.  
  * *Comitato Tecnico \- CTN:* Spiegazione descrittiva e Sezione Team Dinamica con dati importati dal PDF.  
* **Le Associazioni:** Sostituisce "elenco associazioni". Mappa interattiva o lista delle associazioni federate.  
* **Statuto e Regolamenti:** Sostituisce "statuto-federscout".

#### **3\. ATTIVITÀ & FORMAZIONE \- Il Motore Operativo**

*Unificazione di: Scuola Capi, Indaba, Workshop, Assemblee*

* **News & Eventi:** Unico feed che accorpa notizie generali, avvisi e cronaca.  
* **Calendario Formazione:**  
  * *Scuola Capi:* Unica pagina dinamica al posto delle pagine divise per anno. Mostra il prossimo corso e l'archivio storico filtrabile.  
  * *Workshop & Indaba:* Dettagli sui laboratori tecnici.  
  * *Assemblee:* Archivio verbali e convocazioni.

#### **4\. RISORSE & SERVIZI \- Il Valore Aggiunto**

*Nuovo raggruppamento per Feder Letter, Convenzioni, Cerimonie*

* **Feder Letter:** Archivio newsletter e comunicazioni ufficiali.  
* **Convenzioni:** Sottosezione per scontistiche o partnership attive.  
* **Cerimoniale:** Sostituisce "Cerimonie Scout" con testi e guide liturgiche scout.

#### **5\. GALLERIA MULTIMEDIALE \- La Memoria**

*Unificazione di: Gallery, Cartelle annate, Foto Busto B.P.*

* **Foto:** Organizzate per Album ed Evento tramite tag nel DB anziché cartelle fisiche.  
* **Video:** Integrazione playlist YouTube Federscout.

#### **6\. CONTATTI**

* Form di contatto, mappa sede, link social.

## **2\. Stato Attuale del Progetto**

Attualmente il progetto si trova in una fase di transizione critica.

* **Legacy \- Vecchio Sito:** Basato su struttura fisica a cartelle come /2023/ o /2024/ e /wp-content/. Questo approccio rende la manutenzione insostenibile poiché ogni anno richiede la creazione manuale di nuove cartelle.  
* **Target \- Nuovo Sito:**  
  * **Frontend:** In sviluppo separato su framework React, Angular o Vue.  
  * **Backend:** Da costruire da zero in **Java Spring Boot**.  
* **Obiettivo Backend:** Il backend non deve servire pagine HTML statiche ma esporre **API REST JSON** per il Frontend.  
  * *Esempio:* Invece della cartella fisica scuola-capi-2025/index.htm, il Frontend chiederà al Backend GET /api/formazione/corsi?anno=2025 ricevendo i dati dal DB.



