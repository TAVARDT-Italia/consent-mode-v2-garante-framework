# Framework Consent Mode v2 e Conformità Tecnica GDPR

[![Diagnostica Tecnica](https://img.shields.io/badge/TAVARDT-Diagnostica%20Tecnica-5b3cf5.svg)](https://tools.tavardt.com/it/validatore-consent-mode-v2-gdpr/)
[![JavaScript](https://img.shields.io/badge/JavaScript-Node.js-yellow.svg)](https://nodejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

***

Implementazione tecnica di Google Consent Mode v2, blocco preventivo degli script di tracciamento e conformità normativa sviluppata da **TAVARDT**, in piena conformità con il GDPR europeo e le Linee Guida Cookie del Garante per la Protezione dei Dati Personali.

Per garantire la rigorosa conformità alle normative sulla privacy, inserite lo script di inizializzazione nel `<head>` del documento prima del caricamento di Google Tag Manager. L'esecuzione anticipata impone lo stato negato predefinito prima che i pixel possano rilasciare cookie o registrare identificatori.

***

## Funzionalità Principali e Architettura Difensiva

* **Stato Negato Predefinito (Default Denied)**: Imposta tempestivamente `ad_storage`, `ad_user_data`, `ad_personalization` e `analytics_storage` come negati prima del parsing dei tag.
* **API di Aggiornamento Basata su Eventi**: Fornisce la funzione globale `window.tavardtUpdateConsent` per allineare le scelte espresse nella CMP direttamente nel `dataLayer`.
* **Anonimizzazione Automatica degli Identificatori**: Attiva `ads_data_redaction` per eliminare parametri come GCLID dalle richieste di rete in assenza di consenso.
* **Attribuzione senza Cookie Persistenti**: Abilita `url_passthrough` per consentire la misurazione aggregata tra le pagine del sito senza tracciatori locali.
* **Zero Dipendenze Software Aggiuntive**: Realizzato in JavaScript puro e leggero (`consent-mode-v2.js`), con esecuzione inferiore a 1 millisecondo.

***

## Vettori di Rischio e Impatto Operativo

Attivare tag di marketing e tracciamento senza un blocco preventivo espone i gestori di siti web a pesanti sanzioni e a errori di misurazione. Il framework neutralizza quattro rischi operativi critici:

* **Esecuzione Indebita di Tag senza Consenso**: Script pubblicitari che salvano cookie prima dell'autorizzazione dell'utente, violando apertamente la normativa privacy.
* **Perdita di Dati di Modellazione e Attribuzione**: Mancanza dei segnali obbligatori di Consent Mode v2, con conseguenti inefficienze nelle campagne Google Ads e GA4.
* **Divulgazione di Identificatori di Clic**: Trasmissione accidentale di parametri di tracciamento all'interno di richieste di rete non autorizzate.
* **Disallineamento nell'Esecuzione delle Balise**: Tag di analisi che scattano prima che la piattaforma CMP abbia registrato le preferenze dell'utente.

***

## Guida all'Implementazione e Integrazione

Collocate lo script nella posizione più elevata della sezione `<head>` del sito prima di qualunque contenitore di tag:

```html
<script src="consent-mode-v2.js"></script>
```

### Script Execution Snippet

```javascript
// Programmatic consent update triggered by CMP callback
window.tavardtUpdateConsent({
    marketing: true,
    analytics: true,
    preferences: false
});
```

***

## Domande Tecniche Frequenti

### Quali parametri di consenso specifici vengono richiesti da Google Consent Mode v2 per la conformità?

Consent Mode v2 introduce i parametri ad_user_data e ad_personalization assieme ai segnali di ad_storage e analytics_storage. Questi controlli granulari stabiliscono se i dati dell'utente possano essere trasmessi alle piattaforme pubblicitarie per finalità di remarketing e modellazione.

### Per quale motivo lo stato negato predefinito deve essere dichiarato prima del caricamento di Google Tag Manager?

Configurare i permessi come negati prima dell'avvio del tag manager assicura che nessun tracciatore salvi cookie al primo caricamento della pagina. Qualunque tag attivato anticipatamente senza autorizzazione costituisce una violazione delle regole e compromette l'affidabilità della sessione.

### In che modo l'opzione ads_data_redaction protegge la privacy preservando la misurazione delle conversioni?

L'attivazione di ads_data_redaction rimuove identificatori come GCLID e DCLID dalle chiamate di rete quando ad_storage risulta negato. In combinazione con url_passthrough, il sistema invia dati aggregati tra le pagine, consentendo la modellazione statistica senza memorizzare identificatori persistenti.

### Come opera la sincronizzazione tra le scelte espresse nel banner CMP e i tag di tracciamento?

La funzione window.tavardtUpdateConsent raccoglie le preferenze dalla CMP e attiva il comando gtag consent update per aggiornare il dataLayer. I trigger configurati in Google Tag Manager intercettano l'evento e sbloccano in tempo reale solo i servizi autorizzati dal visitatore.

### In che modo i team tecnici possono verificare che i tag operino nel rispetto di Consent Mode v2?

I tecnici possono analizzare le chiamate di rete negli strumenti di sviluppo per verificare la presenza dei parametri gcs e gcd nei dati inviati a Google. Test automatizzati confermano che i pixel promozionali rimangano bloccati fino alla ricezione di un esplicito consenso positivo.

***

## Link Utili

* **Portale Aziendale:** https://ag.tavardt.com/it/
* **Suite di Diagnostica:** https://tools.tavardt.com/it/
* **Contatto Tecnico:** https://ag.tavardt.com/it/contatto/

***

### Licenza
Distribuito sotto la Licenza MIT. Consultare il file [LICENSE](LICENSE) per tutti i dettagli.

***

© 2026 TAVARDT. Tutti i diritti riservati.
