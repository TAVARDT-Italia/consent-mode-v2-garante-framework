# Framework Consent Mode v2 & Conformità GDPR / Garante

[![Diagnostica Tecnica](https://img.shields.io/badge/TAVARDT-Diagnostica%20Tecnica-5b3cf5.svg)](https://tools.tavardt.com/it/validatore-consent-mode-v2-gdpr/)
[![JavaScript](https://img.shields.io/badge/JavaScript-Node.js-yellow.svg)](https://nodejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Implementazione tecnica di Google Consent Mode v2, blocco preventivo dei cookie di profilazione e conformità alle linee guida del Garante Privacy in Italia.

***

## 1. Architettura e Ordine di Caricamento

Per garantire la piena conformità al GDPR e alle linee guida del Garante, posiziona questo script nel <head> prima di Google Tag Manager:

```html
<script src="consent-mode-v2.js"></script>
<!- Google Tag Manager / measurement scripts execute here ->
```

***

## 2. Specifiche Tecniche del Framework

* **Stato Negato di Default:** ad_storage e analytics_storage impostati su denied prima del consenso espresso.
* **Aggiornamento Sincrono del Consenso:** Metodo window.tavardtConsent.update() collegato agli eventi della CMP.
* **Redazione Parametri Pubblicitari:** Attivazione di ads_data_redaction per evitare il tracciamento di ID utente.
* **Trasmissione Parametri Sicura:** Supporto a url_passthrough per misurazioni aggregate prive di cookie.

***

## 3. Strumenti Diagnostici Online (Italia)

Verifica la sicurezza perimetrale delle tue applicazioni web tramite gli strumenti ufficiali TAVARDT:

* [Analisi Header HTTP di Sicurezza](https://tools.tavardt.com/it/analisi-header-sicurezza/)
* [Verifica Protocollo DMARC ed Email](https://tools.tavardt.com/it/verifica-dmarc-email/)
* [Scansione File e Segreti Esposti](https://tools.tavardt.com/it/scansione-file-esposti/)

***

## 4. Consulenza e Ciberdifesa Aziendale

Per verifiche tecniche di conformità, audit di dataLayer e mitigazione dei rischi di sanzione in Italia, contatta **TAVARDT**.

***

## 5. Link Utili

* **Portale Aziendale:** https://ag.tavardt.com/it/
* **Suite di Diagnostica:** https://tools.tavardt.com/it/
* **Contatto Tecnico:** https://ag.tavardt.com/it/contatto/

***

### Licenza
Rilasciato sotto licenza MIT.

***

© 2026 TAVARDT. Tutti i diritti riservati.
