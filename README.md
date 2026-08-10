# BLOCK-LIST-FIREWALLS

Lista de endereços **BLOCK** — IPs que atacaram os firewalls Verkom, gerada
automaticamente pelo auto-block (Wazuh → FortiGate) e sincronizada com este
repositório a cada ciclo de 10 minutos.

## Arquivos

| Arquivo | Conteúdo | Formato |
|---|---|---|
| `blocklist.txt` | IPs bloqueados por brute force (MSSQL/SSH/FTP/RDP) | 1 IPv4 por linha |
| `feed.json` | Metadata (gerado em, fonte, firewalls, contagem) | JSON |

## Formato

- 1 item por linha, linhas com `#` são comentários
- `blocklist.txt`: IPv4 puro (`203.0.113.7`)
- Atualizado automaticamente a cada ciclo do auto-block (10 min) quando há mudança

## Fontes

- **Block:** IPs ativos no `BLOCK-AUTO` dos FortiGates EVEO e VERKOM-200F
  (state files do auto-block — `/opt/chat/data/block_sources_state*.json`)

## Consumo

Consumidores externos (firewalls, SOAR, scripts) podem ler o `blocklist.txt` via
raw URL do GitHub e comparar com o hash do `feed.json`.

**Repo irmão (allow):** [verkombr/ALLOW-LIST-FIREWALLS](https://github.com/verkombr/ALLOW-LIST-FIREWALLS)

> ⚠️ Repositório PRIVADO — acesso restrito ao time Verkom.
