# 🥗 One State Packages - Dieta package with Dieta Card

Una card Lovelace personalizzata per gestire e visualizzare la dieta settimanale direttamente da Home Assistant, e un bot interattivo su Telegram per controllare la dieta!

🇬🇧 Guide in english ![HERE](README_en.md)


<table width="100%">
  <tr>
    <td align="center" width="50%"><strong>Full View</strong></td>
    <td align="center" width="50%"><strong>Compact View</strong></td>
  </tr>
  <tr>
    <td align="left">
      <img src="images/gif1.gif" alt="gif1" width="300" />
    </td>
    <td align="right">
      <img src="images/gif2.gif" alt="gif2" width="300" />
    </td>
  </tr>
</table>


## 🚀 Descrizione

Questo package permette di:
- Gestire la dieta giornaliera e settimanale tramite un’interfaccia moderna e semplice.
- Salvare e visualizzare i pasti giornalieri (colazione, pranzo, cena, snack).
- Gestire la dieta tramite un bot creato dal package usando Telegram Bot!

## 📂 Installazione

### 1. Copia i file nel tuo Home Assistant

- **dieta_it.yaml**: in `config/packages/package_dieta/` (o altro percorso dei package)

### 2. Aggiungi il package alla tua configurazione

Nel tuo `configuration.yaml` aggiungi (se non già presente):

```yaml
homeassistant:
  packages: !include_dir_named packages
```

Verifica che il package venga caricato correttamente.

### 3. Importa la Lovelace Card
Installazione Automatica:

[![Open your Home Assistant instance and open a repository inside the Home Assistant Community Store.](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=OneStatePackages&repository=ha-dieta-card&category=plugin)

Installazione Manuale:
```yaml
resources:
  - url: /local/dieta-card.js
    type: module
```

## ⚙️ Configurazione

1. **Carica il package `dieta_it.yaml`**
   - Questo file crea tutti i sensori, input_text e script necessari alla gestione della dieta.

2. **Personalizza i parametri**
   - L'unica personalizzazione richiesta è il tuo chat_id di Telegram
     ```
     setting:
       chat_id telegram: &chat_id 1234567890 # <-------- Inserisci il tuo chat_id qui
     ```

3. **Aggiungi la card alla dashboard**
   - Vai in Lovelace, scegli "Aggiungi Scheda" → "Dieta Card":
   - Personalizza la tua dieta compilando dall' editor visuale.
  
## 📝 Utilizzo Editor

- **Temi**: Seleziona il tema che piu ti piace tra: `default`, `dark`, `pastel`, `neon`
- **Selezione Giorno**: Seleziona il giorno da compilare.
- **Inserimento pasti**: tramite la card è possibile inserire e salvare i pasti della giornata o della settimana.
- **Salvataggio**: ⚠️ Il pulsante "Salva Giorno" e "Resetta Giorno" azzerano i campi di testo ogni volta, quindi assicurati di salvare la tua dieta per praticità, prima in un file di testo, e poi incollarla nei campi di testo!
  Una volta compilato il giorno, premi "Salva Giorno" e comparirà nella card.


## 2️⃣ Come configurare il bot Telegram

### a. Registrazione del bot

1. Cerca “@BotFather” su Telegram.
2. Avvia la chat e segui le istruzioni per la creazione del bot.
3. Scegli un nome e un username univoco per il bot.
4. Copia il **Token API** fornito da BotFather (es: `123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11`).

### b. Aggiungi la piattaforma Telegram in Home Assistant

Nel tuo `configuration.yaml`:

```yaml
telegram_bot:
  - platform: polling
    api_key: TUO_TOKEN_API
    allowed_chat_ids:
      - CHAT_ID
```

**Sostituisci** `TUO_TOKEN_API` con il token fornito da BotFather.

### c. Trova il tuo Chat ID

- Cerca "@myidbot" su telegram e scrivi nella chat `/getid`, il bot ti risponderà con il tuo `chat_id`
  
### d. Richiamare il menu su Telegram bot

- Una volta configurato tutto il package, ti basta digitare `/diet` nella chat del tuo bot per richiamare il menu del package!
<table width="100%">
  <tr>
    <td align="left">
      <img src="images/screen.png" alt="png1" width="300" />
    </td>
  </tr>
</table>

## ❓ FAQ

**Non vedo la card!**
- Assicurati che la risorsa JS sia correttamente aggiunta a Lovelace.
- Controlla che la sintassi corretta e che il package sia caricato senza errori.
- Svuota la cache del browser!

**Il testo si tronca o viene tagliato**
- Gli input_text di Home Assistant hanno un limite di 255 caratteri per default.

**Non mi arrivano i messagi su Telegram!**
- Controlla che il servizio "Telegram Bot" sia presente, ti basta andare in Strumenti Sviluppatore - Azioni - Cerca Telegram bot e prova ad inviarti un messaggio cosi:
  ```
  action: telegram_bot.send_message
  data:
    message: Funziono!
  ```
  Se il messaggio arriva, hai configurato correttamente Telegram Bot, quindi ricorntrolla il chat_id nel package!
  
## 🤝 Supporto

Per problemi, apri una issue su GitHub [QUI](https://github.com/OneStatePackages/ha-dieta-package/issues).
