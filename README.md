# DuduGymTracker

App pessoal de treino — dashboard, planos A/B/C, wellness pré/pós-treino, análise, histórico e nutrição.
Guarda todos os dados no `localStorage` do browser (nada sai do telemóvel).

## Ficheiros desta pasta

- `index.html` — a aplicação (HTML + CSS + JS num único ficheiro)
- `manifest.json` — descrição da app para instalação no ecrã principal (ícone, nome, cor de tema)
- `sw.js` — service worker, permite a app abrir mesmo sem internet depois da primeira visita
- `icon-180.png`, `icon-192.png`, `icon-512.png`, `icon-1024.png` — ícones da app
- `README.md` — este ficheiro

## Porque é preciso hospedar esta pasta

O manifest.json e o service worker só funcionam em `https://` (ou `localhost`) — é uma regra de segurança do próprio iOS/Safari, não uma limitação desta app. Abrir o `index.html` diretamente do Ficheiros (`file://`) não ativa o ícone nem o modo offline; a app abre mas sem esses extras.

Por isso esta pasta precisa de ficar num servidor com `https://`. Não precisa de ser um servidor complexo — qualquer alojamento de ficheiros estáticos serve, incluindo:

- GitHub Pages (gratuito, sem instalar nada no telemóvel)
- Cloudflare Pages (gratuito)
- Netlify (gratuito, sem conta se usares o "drop")
- Qualquer hosting que já uses

## Instalar no iPhone depois de hospedado

1. Abre o link `https://...` no **Safari** (tem de ser Safari, não outro browser nem a app Claude)
2. Toca no ícone de **Partilhar** (quadrado com seta a subir)
3. **"Adicionar ao Ecrã Principal"**
4. Confirma o nome "DuduGymTracker" e toca em **Adicionar**

A partir daí abre com o ícone dourado, sem barra do Safari, e continua a funcionar mesmo com o telemóvel offline (depois da primeira abertura).

## Atualizar a app no futuro

1. Substitui o `index.html` desta pasta pela versão nova
2. Sobe novamente para o mesmo alojamento (o link não muda)
3. No iPhone, abre a app instalada — o service worker atualiza-se sozinho em segundo plano (pode precisar de fechar e reabrir a app uma vez)
4. Os dados guardados (peso, treinos, histórico) mantêm-se — ficam no `localStorage`, não são apagados por atualizares o ficheiro
