ï»¿# IA privada em 3 nêÂ­veis ê¢â¬â sua IA, na sua mêÂ¡quina, ligada o tempo todo

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


[![IA privada em 3 nêÂ­veis](guia/assets/banner.jpg)](https://inematds.github.io/ia-privada-3-niveis/guia/)

**ê°Å¸â¡Â§ê°Å¸â¡Â· [PortuguêÂªs](README.md) êÂ· ê°Å¸â¡Âºê°Å¸â¡Â¸ [English](README.en.md) êÂ· ê°Å¸â¡Âªê°Å¸â¡Â¸ [EspaêÂ±ol](README.es.md)**

## O que êÂ©

Kit gratuito do INEMA para ter um modelo de IA que **nêÂ£o manda nada para fora** ê¢â¬â e que vocêÂª pode usar do
celular, de qualquer lugar. Ele escolhe o modelo certo para a sua mêÂ¡quina (normal ou sem censura), mede a
velocidade, confere se a porta estêÂ¡ fechada e mostra dois jeitos de deixar a IA sempre ligada: a placa de
vêÂ­deo de casa pelo Tailscale, ou um modelo pequeno numa VPS. Tudo medido de verdade, com os nêÂºmeros no guia.

## ê°Å¸ââ Guia de uso

**https://inematds.github.io/ia-privada-3-niveis/guia/**

## Os 3 nêÂ­veis

| NêÂ­vel | Onde o modelo roda | O que vocêÂª paga | Onde estêÂ¡ |
|---|---|---|---|
| 1 êÂ· API | servidor de outra empresa | por uso | kit [ia-sem-censura-defensiva](https://inematds.github.io/ia-sem-censura-defensiva/guia/) |
| 2 êÂ· Local | no seu computador | luz e disco | [`kit/guias/2-local.md`](kit/guias/2-local.md) |
| 3 êÂ· Sempre ligada | GPU de casa pelo Tailscale (A) ou VPS sem GPU (B) | nada (A) ou a VPS (B) | [`kit/guias/3-sempre-ligada.md`](kit/guias/3-sempre-ligada.md) |
| + Voz | Jarvis Local com cêÂ©rebro sem censura | nada | [`kit/guias/4-voz-jarvis.md`](kit/guias/4-voz-jarvis.md) |

Antes de tudo: [`kit/USO-RESPONSAVEL.md`](kit/USO-RESPONSAVEL.md) e o quadrante
([`kit/guias/1-quadrante.md`](kit/guias/1-quadrante.md)).

## O processo, do inêÂ­cio ao fim

Quem faz: ê°Å¸Â§Â  vocêÂª numa sessêÂ£o com o assistente êÂ· ê¢Å¡â¢ê¯Â¸Â script do kit êÂ· ê°Å¸Â¤â agente/modelo.

| # | Passo | Comando / arquivo | Quem |
|---|---|---|---|
| 1 | Ler as regras | [`kit/USO-RESPONSAVEL.md`](kit/USO-RESPONSAVEL.md) | ê°Å¸Â§Â  |
| 2 | Rodar os testes do kit (offline) | `python3 -m unittest discover -s kit/testes -v` | ê¢Å¡â¢ê¯Â¸Â |
| 3 | Decidir o quadrante | `python3 kit/scripts/quadrante.py` | ê°Å¸Â§Â  + ê¢Å¡â¢ê¯Â¸Â |
| 4 | Instalar o Ollama | `curl -fsSL https://ollama.com/install.sh \| sh` (Linux) ou instalador (Mac/Windows) | ê°Å¸Â§Â  / ê°Å¸Â¤â com o [prompt 01](kit/prompts/01-instalar-e-escolher.md) |
| 5 | Escolher o modelo pela mêÂ¡quina | `python3 kit/scripts/escolhe_modelo.py` | ê¢Å¡â¢ê¯Â¸Â |
| 6 | Baixar e medir | `ollama pull <modelo>` + `python3 kit/scripts/checa_local.py --modelo <modelo>` | ê¢Å¡â¢ê¯Â¸Â |
| 7 | Conferir a porta | `python3 kit/scripts/checa_local.py --so-porta` ê¢â â `loopback` | ê¢Å¡â¢ê¯Â¸Â |
| 8a | Sempre ligada pela GPU de casa | `tailscale serve --bg --tcp 11434 tcp://127.0.0.1:11434` ([prompt 02](kit/prompts/02-casa-pelo-tailscale.md)) | ê°Å¸Â¤â, conferido por ê°Å¸Â§Â  |
| 8b | Sempre ligada numa VPS sem GPU | [prompt 03](kit/prompts/03-vps-sempre-ligada.md) | ê°Å¸Â¤â, conferido por ê°Å¸Â§Â  |
| 9 | Medir de outro aparelho | `checa_local.py --base-url http://100.x.y.z:11434 --modelo <modelo>` | ê¢Å¡â¢ê¯Â¸Â |
| 10 | Voz (opcional) | cêÂ©rebros de [`kit/config/jarvis-cerebros.exemplo.json`](kit/config/jarvis-cerebros.exemplo.json) no Jarvis Local | ê°Å¸Â§Â  |

## Requisitos

Python 3.10+ (sêÂ³ biblioteca padrêÂ£o), Ollama, e ê¢â¬â para o nêÂ­vel 3 ê¢â¬â uma conta gratuita no Tailscale. Para o
caminho B, uma VPS Ubuntu com 8 GB de RAM ou mais.

## LicenêÂ§a

MIT ê¢â¬â veja [LICENSE](LICENSE).

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>