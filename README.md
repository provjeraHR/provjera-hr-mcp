# provjera-hr-mcp

MCP server for Croatian company data from [provjera.hr](https://provjera.hr). Search by name, OIB or MBS from Claude, ChatGPT, Cursor and other AI tools.

MCP poslužitelj za podatke o hrvatskim tvrtkama i udrugama.

The server is hosted. There is nothing to install.

- Endpoint: `https://provjera.hr/mcp` (Streamable HTTP)
- Auth: `Authorization: Bearer <key>`, the same key as the REST API at `https://provjera.hr/v1`
- Free key: [provjera.hr/api-i-podaci/kljuc](https://provjera.hr/api-i-podaci/kljuc)
- Plans and limits: [provjera.hr/api-i-podaci](https://provjera.hr/api-i-podaci)

## Connect

Claude Code:

```bash
claude mcp add --transport http provjera-hr https://provjera.hr/mcp --header "Authorization: Bearer pvj_live_..."
```

Clients with a JSON config:

```json
{
  "mcpServers": {
    "provjera-hr": {
      "url": "https://provjera.hr/mcp",
      "headers": { "Authorization": "Bearer pvj_live_..." }
    }
  }
}
```

## Tools

| Tool | What it returns | Plan |
|---|---|---|
| `search` | Companies by name, OIB or MBS | Free |
| `get_company` | Registry profile, LEI, seat coordinates; Lite adds proceedings, bankruptcy notices, filed statements, latest revenue and profit | Free |
| `get_association` | Udruga by OIB; Lite adds activities and role counts | Free |
| `get_court_notices` | e-Oglasna bankruptcy notices | Lite |
| `get_financials` | FINA headline figures in EUR, every verified year | Standard |
| `get_licences` | Regulator registers: NRCP, HAKOM, HERA, HANFA, HNB, AEM, MUP, Veterinarstvo, RKPFI, Carinska uprava, Registar koncesija | Standard |
| `get_public_funding` | APPRRR subsidies and TED award notices | Standard |
| `get_usage` | The key's plan and this month's usage | Free |

All tools are read-only. No personal data.

## Data sources

Sudski registar RH, FINA RGFI javna objava, Registar udruga, e-Oglasna ploča sudova, APPRRR Baza korisnika potpora, TED (Službeni list Europske unije), Nacionalni registar cestovnih prijevoznika, HANFA, HNB, HAKOM and HERA public registers, GLEIF LEI registar, and more.

Data by [provjera.hr](https://provjera.hr). Unofficial, not affiliated with Ministarstvo pravosuđa, FINA or any other source.
