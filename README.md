# pp-secure-score-connector
# Microsoft Secure Score – Power Platform custom connector

Bring your **Microsoft Secure Score** into Power Apps and Power Automate.
This custom connector calls the Microsoft Graph Security API, so you can show your score, track it over time and build your own security dashboards with low code.

▶️ **Watch the walkthrough:** [Power Apps + Custom Connector | Integrate Microsoft Secure Score](https://www.youtube.com/watch?v=OqNpn-Pca7g)

---

## What's included

| File | What it is |
|---|---|
| `secure-score-connector.swagger.json` | The custom connector definition (OpenAPI 2.0) |

## What you can do with it

- Read your current Secure Score and the maximum possible score
- Get the score history, day by day
- Use the data in a Power Apps dashboard or a Power Automate flow (for example a weekly score email)

## Requirements

- **Power Apps or Power Automate with a premium licence** (custom connectors are premium)
- **An Entra ID app registration** in your tenant, with the Microsoft Graph application permission **`SecurityEvents.Read.All`** and admin consent
- Permission to create custom connectors in your Power Platform environment

## Setup

### 1. Create the app registration
1. Go to the **Microsoft Entra admin center** › **App registrations** › **New registration**
2. Name it (for example `SecureScore-Connector`), single tenant, and register it
3. **API permissions** › **Add a permission** › **Microsoft Graph** › **Application permissions** › `SecurityEvents.Read.All` › **Grant admin consent**
4. **Certificates & secrets** › **New client secret**. Copy the value now: you can't see it again.
5. Note the **Application (client) ID** and the **Directory (tenant) ID**

### 2. Create the connector
1. Download `secure-score-connector.swagger.json` from the [latest release](../../releases/latest)
2. In [make.powerapps.com](https://make.powerapps.com): **Custom connectors** › **New custom connector** › **Import an OpenAPI file**
3. On the **Security** tab, enter your own **Client ID**, **Client secret** and tenant details
4. **Create connector**, then copy the **Redirect URL** it shows into your app registration (**Authentication** › **Add a platform** › **Web**)

### 3. Test it
1. On the **Test** tab, create a **new connection**
2. Run the operation that lists Secure Scores. A `200` response with score data means it works.

## Good to know

- Secure Score data is read-only through this connector
- Never commit your client secret to a repository or share it in an app
- For production, use a **certificate** instead of a client secret, and store secrets in **Azure Key Vault**

## Need help?

Want this set up in your tenant, extended with your own dashboard, or connected to several tenants?
**depluy** builds and supports Power Platform solutions and trains your team to own them.

👉 **[depluy.com](https://depluy.com)** · contact@depluy.com

---

Licensed under the [MIT License](LICENSE). Not affiliated with or endorsed by Microsoft.
