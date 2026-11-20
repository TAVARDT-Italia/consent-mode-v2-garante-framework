# Framework Consent Mode v2 & Linee Guida Garante Privacy | TAVARDT Italia

[![Validador de Consentimento](https://img.shields.io/badge/TAVARDT-Diagn%C3%B3stico%20T%C3%A9cnico-5b3cf5.svg)](https://tools.tavardt.com/it/validatore-consent-mode-v2-gdpr/)
[![Conformidade](https://img.shields.io/badge/Jurisdi%C3%A7%C3%A3o-Italia-00C853.svg)](https://ag.tavardt.com/it/sicurezza-informatica/)

Implementazione tecnica di Google Consent Mode v2, blocco preventivo dei cookie di terze parti e conformità alle linee guida del Garante Privacy in Italia.

Desenvolvido e mantido pela divisão de privacidade digital e engenharia de dados da **[TAVARDT Italia](https://ag.tavardt.com/it/)**.

---

## 1. Architettura e Ordine di Esecuzione

Per garantire la piena conformità con i provvedimenti del Garante, inserire questo modulo all'interno dell'<head> prima del caricamento di Google Tag Manager:

```html
<script src="consent-mode-v2.js"></script>
<!-- O contentor do Google Tag Manager ou scripts de medição seguem aqui -->
```

---

## 2. Caratteristiche Tecniche Implementate

* **Blocco Preventivo 'Denied':** Imposta i parametri ad_storage, analytics_storage e ad_user_data su 'denied' all'avvio.
* **Metodo di Aggiornamento del Consenso:** Fornisce la funzione window.tavardtUpdateConsent() che notifica l'evento tavardt_consent_updated nel dataLayer.
* **Offuscamento Dati Pubblicitari:** Abilita ads_data_redaction per rimuovere identificatori di clic quando il consenso marketing è negato.
* **Collegamento Sicuro tra Domini:** Attiva url_passthrough garantendo la misurazione senza memorizzazione non autorizzata sul dispositivo.

---

## 3. Documentazione e Checklist di Conformità

Consulte a lista detalhada de requisitos técnicos para este país:

* [Checklist Técnico de Conformidade](checklist.md)

---

## 4. Strumenti Diagnostici Online (Italia)

Audite a conformidade das suas etiquetas e proteja o seu domínio com ferramentas online verificadas:

* [Validatore Consent Mode v2 e GDPR](https://tools.tavardt.com/it/validatore-consent-mode-v2-gdpr/)
* [Analisi Header HTTP di Sicurezza](https://tools.tavardt.com/it/analisi-header-sicurezza/)
* [Verifica Protocollo DMARC ed Email](https://tools.tavardt.com/it/verifica-dmarc-email/)
* [Scansione File e Segreti Esposti](https://tools.tavardt.com/it/scansione-file-esposti/)
* [Suite Diagnostica Completa Italia](https://tools.tavardt.com/it/)

---

## 5. Consulenza e Governance delle Etichette

Per audit di conformità al Garante Privacy, ottimizzazione del tagueamento e consulenza tecnica in Italia, contatta **[TAVARDT Italia](https://ag.tavardt.com/it/contatti/)**.
