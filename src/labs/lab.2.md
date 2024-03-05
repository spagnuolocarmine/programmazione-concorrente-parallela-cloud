# Programmazione Concorrente, Parallela e su Cloud
## Lab assignment 1

### 1️⃣  **Registrazione a GCP**
1. Accedere al link all'interno della mail ricevuta dal professore. Inserire all'interno della pagina il proprio nome e l'email istituzionale _studenti.unisa.it_ e premere il tasto _Submit_;
2. accedere al link di verifica all'interno della mail ricevuta da Google sul proprio account istituzionale ed effettuare la verifica. Verrà inviata un'altra mail sul proprio account contenente un codice coupon e un link per riscattarlo, tuttavia, non è possibile riscattare il coupon sull'account Google istituzionale per problemi tecnici. Salvare il codice coupon;
3. utilizzare il link https://cloud.google.com/ per accedere con un account Google personale usando il bottone in alto a destra;
4. utilizzare il link https://console.cloud.google.com/education?authuser=0 per accedere alla pagina dove riscattare il proprio codice. **NOTA BENE:** l'ultimo numero indicato nel link deve corrispondere all'account Google PERSONALE e non a quello istituzionale. È possibile controllare il numero associato ad ogni account Google controllando il link dopo aver effettuato l'accesso con l'account personale (passo 3); in caso in cui non si riesca ad accedere al link indicato, disconnettere tutti gli account Google, riavviare il browser, effettuare l'accesso SOLO CON L'ACCOUNT PERSONALE e riprovare;
5. inserire il codice ricevuto tramite mail (passo 2) nel campo _Codice Coupon_, accettare e proseguire. La pagina re-indirizzerà automaticamente alla dashboard _Fatturazione_ dove saranno visualizzati i 50$ a disposizione.  


### 2️⃣  **Creazione di una Macchina Virtuale tramite Console Web**
1. Accedere alla console GCP utilizzando l'account Google personale. Accedere al sito https://cloud.google.com/, se necessario, accedere con l'account personale e cliccare sul bottone _Console_ in alto a destra;
2. utilizzare la barra di ricerca in alto per accedere al servizio _VM Instances_. In caso venga richiesto di selezionare un account di fatturazione, selezionare l'_Account Studente_;
3. **SOLO AL PRIMO ACCESSO AL SERVIZIO** cliccare il tasto _Abilita_ e attendere l'attivazione. La pagina re-indirizzerà automaticamente alla dashboard di _Compute Engine_;
4. **SOLO PER LA PRIMA CREAZIONE** le istanze GCP richiedono di fornire una propria chiave ssh al momento della creazione per l'accesso che potrà essere riutilizzata ad ogni creazione di istanza successiva. Le istruzioni per creare una nuova chiave sulla propria macchina sono disponibili nella documentazione ufficiale di GCP https://cloud.google.com/compute/docs/connect/create-ssh-keys#create_an_ssh_key_pair/ ;
5. nella dashboard di _Compute Engine_ utilizzare il bottone _Crea istanza_ per creare una nuova macchina virtuale;
6. nel campo _Regione_ selezionare una delle seguenti opzioni in modo da usufruire del piano gratuito:
	- Oregon: us-west1
	- Iowa: us-central1
	- South Carolina: us-east1
7. nel campo _Tipo di macchina_ selezionare _e2-micro_;
8. nel campo _Disco di avvio_, utilizzare il tasto _Cambia_ per selezionare come _Sistema operativo_ _Ubuntu_ con _Versione_ _Ubuntu 18.04 LTS_;
9. nel campo _Firewall_ spuntare entrambe le opzioni;
10. aprire la sezione _NETWORKING, DISCHI, SICUREZZA, GESTIONE, SINGLE-TENANCY"_;
11. aprire la sezione _Sicurezza_ - _Gestisci accesso_ e usare il bottone _Aggiungi elemento_ per inserire la chiave ssh generata (passo 4). Inserire nel campo _Chiave SSH 1_ il contenuto del file _.pub_. **N.B.** L'ultima parte del file contiene l'username da utilizzare per accedere all'istanza tramite ssh;
12. aprire la sezione _Gestione_ e selezionare _Spot_ nel campo _Modello di provisioning delle VM_;
13. Creare l'istanza usando il tasto _Crea_ e attendere per l'avvio. Una volta che l'istanza è in esecuzione utilizzare il protocollo ssh per accedere utilizzando l'IP esterno. **NB** Per accedere all'istanza è necessaria la chiave privata (passo 4) ovvero il file senza l'estensione _.pub_. Il comando per l'accesso deve avere la seguente sintassi:
```ssh -i ssh-key-private-file-name sshkey-username@99.999.9.99```;
Ulteriori informazioni riguardo la connessione ad una macchina virtuale sono disponibili nella documentazione ufficiale di GCP https://cloud.google.com/compute/docs/instances/connecting-advanced#thirdpartytools/.
**ATTENZIONE:** Una volta terminato di lavorare sulle macchine virtuali è importante ricordarsi di eliminarle per evitare di esaurire il credito a disposizione. Per farlo tramite la dashboard di _Compute Engine_ selezionare l'istanza da eliminare, cliccare sui tre puntini in alto e selezionare _Elimina_.
**Installazione MPI** L'installazione di MPI su un'istanza creata in questo modo è disponibile sul repository Github https://github.com/spagnuolocarmine/ubuntu-openmpi-openmp/.

### 3️⃣  **Installazione e configurazione Google gcloud**

- [gcloud CLI overview ](https://cloud.google.com/sdk/gcloud)
- [How-to Guides](https://cloud.google.com/sdk/docs/how-to)
- [Machine families](https://cloud.google.com/compute/docs/machine-types)

### 4️⃣ **Creazione di una Home Page personale**

1. Avviare una instanza e2-micro seguendo la procedura 2 **Creazione di una macchina virtuale da Console Web**;
2. collegarsi tramite ```ssh``` all'istanza ed effettuare gli aggiornamenti 
	```$ sudo apt-get update && sudo apt-get upgrade -y```;
3. installare Apache Web Server: 
	```$ sudo apt-get install apache2 -y```;
4. modificare il file ```index.html``` in ```/var/www/html``` con una messaggio di esempio;
5. connettersi da browser utilizzando l'IP pubblico dell'istanza e verificare che il contenuto della pagina corrisponda;
6. **NOTA BENE:** se non è possibile connettersi all'istanza in questo modo verificare le impostazioni nel campo *Firewall* usate durante la creazione della macchina;
7. eliminare l'instanza.

Ripetere l'esercizio utilizzando la Web console.



### 5️⃣ **Creazione di un cluster di instanze e2-micro**

![sshkey](https://community-cdn-digitalocean-com.global.ssl.fastly.net/variants/DLcPFpLdv6EiPrU3x65LSQYe/035575f2985fe451d86e717d73691e533a1a00545d7230900ed786341dc3c882)

1. Creare 4 istanze e2.micro;
2. avviare una nuova sessione remota tramite ```ssh``` per ogni macchina creata ed effettuare gli aggiornamenti 
	```$ sudo apt-get update && sudo apt-get upgrade -y```;
3. _su ogni istanza_ creare un nuovo utente con username _pcpc_:
	```$ sudo useradd -s /bin/bash -d /home/pcpc/ -m -G sudo pcpc```
	ed impostare la password:
	```$ sudo passwd pcpc```;
4. _su ogni istanza_ accedere all'account _pcpc_:
	```$ sudo login pcpc```
5. _su ogni istanza_ modificare il file di configarezione di ssh:
	```$ sudo vim /etc/ssh/sshd_config ```
	e cambiare l'opzione _PasswordAuthentication_ come segue:
	```PasswordAuthentication yes```
6. _su ogni istanza_ riavviare il servizio ssh:
	```$ sudo service ssh restart```
6. scegliere un'istanza da usare come MASTER e generare una coppia di chiavi ssh:
	```$ ssh-keygen -t rsa```;
7. _sull'istanza MASTER_ aggiungere la chiave pubblica appena generata alle authorized_keys:
	```$ cat ~/.ssh/id_rsa.pub >>  ~/.ssh/authorized_keys```;
8. _sull'istanza MASTER_ aggiungere la coppia di chiavi ssh ad ogni istanza alle authorized_keys:
	```$ cat ~/.ssh/id_rsa.pub | ssh pcpc@IP_INSTANCE "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >>  ~/.ssh/authorized_keys"```;
9. _su ogni istanza_ verificare di riuscire ad avviare una nuova sessione remota tramite ssh da ogni istanza verso le altre senza utilizzare nome utente e password:
	```$ ssh IP```;