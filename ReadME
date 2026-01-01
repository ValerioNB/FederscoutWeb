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

## **3\. Guida alla Progettazione Backend \- Spring Boot**

*Come iniziare su IntelliJ IDEA per gettare le basi solide.*

### **A. Preparazione Ambiente IntelliJ IDEA**

1. Crea un **New Project** con **Spring Initializr**.  
2. **Dependencies** da selezionare subito:  
   * Spring Web per le API REST.  
   * Spring Data JPA per il database.  
   * MySQL Driver o PostgreSQL a seconda del DB scelto.  
   * Lombok per pulire il codice da getter e setter.

### **B. Struttura delle Cartelle \- Package Structure**

Utilizzare l'inglese per standard internazionale e seguire il pattern **Layered Architecture**.

Creare questi package dentro com.federscout.backend:

1. 📂 **controller**  
   * *Funzione:* Entry Point API REST. Ricevono le richieste HTTP, validano l'input e delegano al Service Layer.  
   * *File Esempio:* NewsController.java, AssociationController.java, TrainingController.java.  
2. 📂 **service**  
   * *Funzione:* Business Logic Layer. Implementa le regole di dominio, gestisce le transazioni e coordina i dati.  
   * *File Esempio:* NewsService.java, EmailService.java.  
3. 📂 **repository**  
   * *Funzione:* Interfaccia con il Database e query SQL.  
   * *File Esempio:* NewsRepository.java che estende JpaRepository.  
4. 📂 **model** o entity  
   * *Funzione:* Rappresentazione delle tabelle del DB.  
   * *File Esempio:* News.java, Association.java, ScoutEvent.java.  
5. 📂 **dto** \- Data Transfer Object  
   * *Funzione:* Oggetti per il trasferimento dati. Disaccoppiano il database dall'API pubblica per sicurezza ed efficienza.  
   * *File Esempio:* EventSummaryDTO.java.

### **C. Logica di Business e Beans \- Esempi Pratici**

Traduzione delle cartelle del vecchio sito in Logica Java.

#### **1\. Gestione "Scuola Capi" e "Eventi"**

Evitare classi diverse per ogni anno.

* **Entity ScoutEvent:** Campi previsti quali id, title, description, date, type, location. Il campo type userà un ENUM con valori SCHOOL, ASSEMBLY, WORKSHOP.  
* **Logic:** Il frontend filtrerà per data o tipo.  
* **Bean Logic:** Il @Service implementerà un metodo getUpcomingEvents() che interroga il @Repository con una query findAllByDateAfter usando la data corrente.

#### **2\. Gestione "Chi Siamo" e "Associazioni"**

* **Entity Association:** Campi previsti quali name, region, logoUrl, website, coordinates.  
* **Renaming:** I file vecchi elenco-associazioni/index.htm diventano un endpoint API GET /api/associations.

#### **3\. Gestione "Feder Letter" e "Documenti"**

* **Entity Document:** Campi previsti quali title, category, fileUrl, uploadDate. Category userà un ENUM con valori STATUTE, LETTER, CONVENTION.  
* **Logic:** Permettere l'upload di PDF dal pannello di amministrazione e restituire la lista filtrata per categoria al frontend.

### **D. Tabella di Migrazione \- Naming Convention**

| Vecchia Cartella File System | Nuova Entity Spring Boot | Nuovo Endpoint Controller |
| :---- | :---- | :---- |
| scuola-capi-202x | TrainingCourse | /api/training/courses |
| news / feed | NewsArticle | /api/news |
| elenco-associazioni | Association | /api/associations |
| statuto-federscout | Document \- Type STATUTE | /api/documents/statute |
| gallery / uploads | MediaGallery | /api/gallery |
| comitato-ctm | TeamMember | /api/team |

