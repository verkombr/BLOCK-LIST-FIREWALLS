# VRK-BLOCK-LIST-FIREWALL

Threat feed interno da Verkom — lista de endereços **BLOCK** e **ALLOW** geradas
automaticamente pelo auto-block (Wazuh → FortiGate) e sincronizadas com este
repositório privado.

## Arquivos

| Arquivo | Conteúdo | Formato |
|---|---|---|
| `blocklist.txt` | IPs bloqueados por brute force (MSSQL/SSH/FTP/RDP) | 1 IPv4 por linha |
| `allowlist.txt` | Redes que NUNCA devem ser bloqueadas (infra + RFC1918) | 1 CIDR por linha |
| `feed.json` | Metadata (gerado em, fonte, firewalls, contagem) | JSON |

## Formato

- 1 item por linha, linhas com `#` são comentários
- `blocklist.txt`: IPv4 puro (`203.0.113.7`)
- `allowlist.txt`: CIDR (`177.104.0.0/16`)
- Atualizado automaticamente a cada ciclo do auto-block (10 min) quando há mudança

## Fontes

- **Block:** IPs ativos no `BLOCK-AUTO` dos FortiGates EVEO e VERKOM-200F
  (state files do auto-block — `/opt/chat/data/block_sources_state*.json`)
- **Allow:** whitelist hardcoded do `lib/block_sources.py` (RFC1918 +
  `177.104.0.0/16` WANs Verkom) + whitelist dos configs

## Consumo

Consumidores externos (firewalls, SOAR, scripts) podem ler os arquivos via
raw URL do GitHub e comparar com o hash do `feed.json`.

> ⚠️ Repositório PRIVADO — acesso restrito ao time Verkom.
