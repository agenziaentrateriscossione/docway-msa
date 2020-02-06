# Sistema di Gestione documentale DocWay comprensivo del modulo MSA
___
> #### Per l'installazione di DocWay ed eXtraWay si rimanda alla pagina [riuso](https://github.com/agenziaentrateriscossione/riuso)
___
## Modulo di gestione scambio documenti

#### MSA (Mail Storage Agent) è il software che si occupa dell'archiviazione di messaggi di posta elettronica sul sistema documentale e di protocollo informatico DocWay. Gestisce sia caselle di posta elettronica standard che caselle PEC. Gestisce inoltre l'archiviazione di documenti di protocollo pervenuti tramite interoperabilità tra pubbliche amministrazioni. I protocolli supportati sono IMAP e POP.
___

La posta elettronica non è solo il modo più immediato per comunicare, è anche una risorsa di informazioni tra le più ricche e più importanti in azienda. Le informazioni scambiate tramite posta elettronica generalmente rimangono nella casella postale dei dipendenti e non vengono memorizzate su altri sistemi. Ciò fa sì che le email ricevute e inviate formino un ricco deposito di informazioni che si espande giorno dopo giorno. Questo deposito è gestito da DocWay tramite il modulo MSA.

MSA (Mail Storage Agent) è un servizio Java multi-processo che si occupa delle seguenti operazioni:
* archiviazione delle email PEC e non (le mail vengono trasformate e salvate in documenti in DocWay XML);
* scambio di documenti tra sistemi DocWay XML differenti mediante la posta elettronica certificata (interoperabilità);
* Completa gestione del processo di interfacciamento con lo SdI per le fatture elettroniche.

MSA lavora esaminando periodicamente le caselle di posta (certificate o meno) configurate e dispone di una sua specifica console di amministrazione e controllo.

La sua primaria funzione è quella di monitorare le caselle mail e PEC aziendali e di realizzare una registrazione automatica delle mail e degli allegati digitali, ai fini di una corretta formazione dell'Archivio documentale, secondo modelli definibili dall'utente.

Ogni mail/PEC viene così trasformata in un documento, immediatamente disponibile e correttamente registrato in Archivio. ll documento può essere registrato come documento non protocollato e/o come documento in arrivo in bozza, ovvero può essere automaticamente protocollato, se necessario, così come può essere repertoriato, classificato, fascicolato e assegnato all'interno della Struttura Organizzativa.

Per ogni casella mail/PEC gestita dall'archiviatore è possibile definire il corrispondente processo d'Archivio e di distribuzione interna; così come è possibile la gestione illimitata di caselle mail/PEC per ogni Ente o AOO.

![strutturaMSA](https://user-images.githubusercontent.com/9255029/64540973-6138ba80-d321-11e9-877a-0c850881cb9f.png)

Particolare attenzione è stata data all'individuazione delle modalità operative per la gestione del processo di archiviazione della PEC finalizzato al miglioramento della conservazione digitale a norma mediante specifica gestione dei formati digitali consentiti all'interno di DocWay.

Caso d'uso: qualora il sistema intercetti una email/PEC inviata a più caselle di posta definite per AOO/UOR, è possibile configurare a monte la procedura di archivizione del messaggio, in maniera tale che avvenga la registrazione di un solo documento, con l'assegnazione in Conferenza di Servizi degli altri RPA delle caselle che hanno ricevuto la email/PEC.

Il modulo dispone di una specifica Console che permette di monitorare lo stato dei messaggi archiviati, evidenziando lo stato dell'ultima esecuzione dell'MSA e gli errori riscontrati nello scaricamento dei singoli messaggi email/PEC, suddivisi in base alla casella mail di provenienza.
___
![homeMSA](https://user-images.githubusercontent.com/9255029/64540629-cb049480-d320-11e9-8ccc-a8f6e31611a0.png)
___
Di seguito le funzionalità offerto dal presente modulo:
- Architettura software, modulare, espandibile e facilmente personalizzabile tramite l'implementazione di apposite interfacce per:
    + personalizzare il comportamento di archiviazione di caselle di posta elettronica;
    + leggere le configurazioni delle caselle di posta (e eventualmente estenderle) su sistemi differenti da ACL;
    + archiviare le email su sistemi differenti da DocWay.
- Worker concorrenti in grado di effettuare l'archiviazione in parallelo di più caselle di posta abbattendo i tempi di archiviazione (in particolare nel caso di numerose caselle di posta elettronica da gestire).
- Produzione su MongoDB di rapporti di Audit per ogni sessione di archiviazione di ogni singola casella di posta elettronica. In caso di errore verrà memorizzato l'intero EML per agevolare le operazioni di monitoraggio, controllo errori e eventuale risoluzione di problemi.
- Console WEB di monitoraggio per individuare agevolmente le email che sono andate in errore e per effettuare nuovamente l'elaborazione.
___

### Prerequisiti:
1. _Java8_
2. MongoDB (vers. 3.6.3)

___
### Installazione

Per dettagli sull'installazione del software (configurazione applicativa e dei servizi) consultare il file [INSTALL.md](INSTALL.md).

___
#### Status del progetto:

- stabile

#### Limitazioni sull'utilizzo del progetto:

Il presente modulo della piattaforma documentale è stato realizzato facendo uso di MongoDB. Allo stato attuale, deve essere associato a eXtraWay e MongoDB.

___
#### Detentore del copyright:

Agenzia delle Entrate-Riscossione (ADER)

___
#### Soggetto incaricato del mantenimento del progetto open source:

| 3D Informatica srl |
| :------------------- |
| Via Speranza, 35 - 40068 S. Lazzaro di Savena |
| Tel. 051.450844 - Fax 051.451942 |
| http://www.3di.it |

___
#### Indirizzo e-mail a cui inviare segnalazioni di sicurezza:
tickets@3di.it
