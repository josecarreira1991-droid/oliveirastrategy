# OLIVER — MODO POLÍTICO: oliveirastrategy.com
## Instrução para Claude Code — Quantrex VPS

---

## RESTRIÇÕES ABSOLUTAS

- NÃO TOCAR em nenhum tenant existente
- NÃO TOCAR no DNA/prompt/config atual do Oliver
- NÃO TOCAR em nenhum código em produção
- NÃO ALTERAR tabelas existentes
- NÃO ALTERAR nenhum fluxo de mensagens existente

## GATILHO

O botão WhatsApp do site abre:
`https://wa.me/12398215146?text=Olá%2C+vim+pelo+oliveirastrategy.com`

Primeira mensagem contém: `oliveirastrategy.com`

## IMPLEMENTAÇÃO

### Arquivo novo: political_mode.py
Ver arquivo political_mode.py neste repositório.

### Adição mínima no handler existente

```python
# No topo do arquivo handler:
from political_mode import is_political_contact, get_oliver_prompt

# Logo após definir system_prompt para o Oliver:
if tenant_id == OLIVER_TENANT_ID:
    system_prompt = get_oliver_prompt(incoming_message_text, system_prompt)
```

Isso é tudo. 1 import + 2 linhas. Nada mais é alterado.

## CHECKLIST

- [ ] Localizei arquivo handler de mensagens
- [ ] Sei o OLIVER_TENANT_ID correto
- [ ] Testei political_mode.py isoladamente
- [ ] A mudança são 2 linhas dentro de `if tenant_id == OLIVER_TENANT_ID`
- [ ] Nenhum outro tenant é afetado
- [ ] DNA padrão retorna intacto quando is_political=False
