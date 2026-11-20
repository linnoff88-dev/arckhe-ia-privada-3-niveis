# IA privada em 3 nÃ­veis â€” sua IA, na sua mÃ¡quina, ligada o tempo todo

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


[![IA privada em 3 nÃ­veis](guia/assets/banner.jpg)](https://inematds.github.io/ia-privada-3-niveis/guia/)

**ðŸ‡§ðŸ‡· [PortuguÃªs](README.md) Â· ðŸ‡ºðŸ‡¸ [English](README.en.md) Â· ðŸ‡ªðŸ‡¸ [EspaÃ±ol](README.es.md)**

## O que Ã©

Kit gratuito do INEMA para ter um modelo de IA que **nÃ£o manda nada para fora** â€” e que vocÃª pode usar do
celular, de qualquer lugar. Ele escolhe o modelo certo para a sua mÃ¡quina (normal ou sem censura), mede a
velocidade, confere se a porta estÃ¡ fechada e mostra dois jeitos de deixar a IA sempre ligada: a placa de
vÃ­deo de casa pelo Tailscale, ou um modelo pequeno numa VPS. Tudo medido de verdade, com os nÃºmeros no guia.

## ðŸ“– Guia de uso

**https://inematds.github.io/ia-privada-3-niveis/guia/**

## Os 3 nÃ­veis

| NÃ­vel | Onde o modelo roda | O que vocÃª paga | Onde estÃ¡ |
|---|---|---|---|
| 1 Â· API | servidor de outra empresa | por uso | kit [ia-sem-censura-defensiva](https://inematds.github.io/ia-sem-censura-defensiva/guia/) |
| 2 Â· Local | no seu computador | luz e disco | [`kit/guias/2-local.md`](kit/guias/2-local.md) |
| 3 Â· Sempre ligada | GPU de casa pelo Tailscale (A) ou VPS sem GPU (B) | nada (A) ou a VPS (B) | [`kit/guias/3-sempre-ligada.md`](kit/guias/3-sempre-ligada.md) |
| + Voz | Jarvis Local com cÃ©rebro sem censura | nada | [`kit/guias/4-voz-jarvis.md`](kit/guias/4-voz-jarvis.md) |

Antes de tudo: [`kit/USO-RESPONSAVEL.md`](kit/USO-RESPONSAVEL.md) e o quadrante
([`kit/guias/1-quadrante.md`](kit/guias/1-quadrante.md)).

## O processo, do inÃ­cio ao fim

Quem faz: ðŸ§  vocÃª numa sessÃ£o com o assistente Â· âš™ï¸ script do kit Â· ðŸ¤– agente/modelo.

| # | Passo | Comando / arquivo | Quem |
|---|---|---|---|
| 1 | Ler as regras | [`kit/USO-RESPONSAVEL.md`](kit/USO-RESPONSAVEL.md) | ðŸ§  |
| 2 | Rodar os testes do kit (offline) | `python3 -m unittest discover -s kit/testes -v` | âš™ï¸ |
| 3 | Decidir o quadrante | `python3 kit/scripts/quadrante.py` | ðŸ§  + âš™ï¸ |
| 4 | Instalar o Ollama | `curl -fsSL https://ollama.com/install.sh \| sh` (Linux) ou instalador (Mac/Windows) | ðŸ§  / ðŸ¤– com o [prompt 01](kit/prompts/01-instalar-e-escolher.md) |
| 5 | Escolher o modelo pela mÃ¡quina | `python3 kit/scripts/escolhe_modelo.py` | âš™ï¸ |
| 6 | Baixar e medir | `ollama pull <modelo>` + `python3 kit/scripts/checa_local.py --modelo <modelo>` | âš™ï¸ |
| 7 | Conferir a porta | `python3 kit/scripts/checa_local.py --so-porta` â†’ `loopback` | âš™ï¸ |
| 8a | Sempre ligada pela GPU de casa | `tailscale serve --bg --tcp 11434 tcp://127.0.0.1:11434` ([prompt 02](kit/prompts/02-casa-pelo-tailscale.md)) | ðŸ¤–, conferido por ðŸ§  |
| 8b | Sempre ligada numa VPS sem GPU | [prompt 03](kit/prompts/03-vps-sempre-ligada.md) | ðŸ¤–, conferido por ðŸ§  |
| 9 | Medir de outro aparelho | `checa_local.py --base-url http://100.x.y.z:11434 --modelo <modelo>` | âš™ï¸ |
| 10 | Voz (opcional) | cÃ©rebros de [`kit/config/jarvis-cerebros.exemplo.json`](kit/config/jarvis-cerebros.exemplo.json) no Jarvis Local | ðŸ§  |

## Requisitos

Python 3.10+ (sÃ³ biblioteca padrÃ£o), Ollama, e â€” para o nÃ­vel 3 â€” uma conta gratuita no Tailscale. Para o
caminho B, uma VPS Ubuntu com 8 GB de RAM ou mais.

## LicenÃ§a

MIT â€” veja [LICENSE](LICENSE).

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>