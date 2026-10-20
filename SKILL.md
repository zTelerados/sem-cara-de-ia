---
name: acabamento
description: 'Acabamento de UI: tira a cara de IA de uma interface pronta. Use quando uma interface pronta (site, landing, app, componente) tiver cara de feita por IA, de template ou de genérica e precisar sair com cara de profissional sem ser refeita do zero. Gatilhos: "acabamento", "tira a cara de IA", "deixa profissional", "está genérico", "parece template", "revisa a estética". Não é redesign: preserva estrutura, texto e tudo que já está bom, e troca só o que cai numa das leis.'
license: MIT
metadata:
  author: Kore ID
  version: 1.0.0
---

# Acabamento

A IA entrega rápido e entrega com vícios. Os vícios são sempre os mesmos, dá pra listar, dá pra achar no código e dá pra trocar um por um. Esta skill recebe uma UI pronta e devolve a mesma UI sem eles. Ele nasceu de 973 correções em 150 conversas de site e código: cada lei abaixo é um erro que se repetiu até virar regra.

O acabamento tem quatro movimentos: ler, decidir, executar, provar. E uma lei acima de todas.

## Lei zero: não piora

A correção mais frequente de quem trabalha com IA não é "ficou feio". É "a versão nova ficou pior que a anterior". O acabamento existe pra tirar vício, não pra trocar gosto.

- Antes de tocar em qualquer coisa, escreva o inventário do que fica: seções, mecanismos e detalhes que já funcionam. Esse inventário é intocável durante o trabalho.
- Mude só o que caiu numa lei da seção 1. O que incomoda mas não caiu em lei vira proposta separada, nunca alteração.
- Texto é do dono. Copy existente fica palavra por palavra. Mudança de texto vai como proposta, com o antes e o depois lado a lado.
- Troca de fonte e qualquer assinatura visual nova também vão como proposta. Tipografia passa pelo olho do dono antes de fechar.
- Termina com prova (seção 4). Sem prova não é "pronto".

## 1. Ler: os vícios de cara de IA

Varra o projeto antes de decidir qualquer coisa. Cada achado vira um item numerado com o lugar exato (arquivo e linha, ou seletor).

| Vício | Pista no código | Por que denuncia |
|---|---|---|
| Botão pill nos CTAs | `rounded-full`, `border-radius: 999px` ou `9999px` em `a` e `button` | É o botão padrão de gerador. Canto reto em CTA e aba. |
| Rótulo em caixa alta com tracking em cima do título | `uppercase` + `tracking-[0.2em]`, `letter-spacing: .2em`, texto curto com `·` ou `•` | O título que precisa de legenda em cima não está falando sozinho. |
| Última palavra do título em itálico, outra cor ou outra fonte | `<em>`, `<i>` ou `<span class="text-...">` como último filho de `h1`/`h2` | Ênfase de template. Hierarquia vem de tamanho e peso, não de truque na última palavra. |
| Passo numerado visível | `01`, `02`, `03` em `span` de seção, lista ou acordeão | Padrão de árvore que todo mundo já reconhece. |
| Grid de quatro cards iguais | `grid-cols-4`, `md:grid-cols-4`, quatro blocos ícone + título + texto | A estrutura preguiçosa. Card é o container de quem não decidiu o layout. |
| Gradiente roxo, orbs de luz, mesh gradient | `from-purple`, `from-violet`, `#7c3aed`, `#a855f7`, `radial-gradient` com `blur` grande | A cor padrão da IA. Ninguém escolheu. |
| Bolinha decorativa, ponto pulsando, sparkle | `animate-pulse`, `w-2 h-2 rounded-full`, SVG de estrelinha | Enfeite sem função. |
| Vidro e caixa como decoração | `backdrop-blur` em card parado; card com fundo diferente flutuando sobre o fundo plano | Caixa só existe sobre imagem ou vídeo, onde tem o que separar. |
| Serif display de alto contraste, ou a sans de sempre como voz única | `Instrument Serif`, `Fraunces`, `Playfair`; `Inter` ou `Roboto` como única família | A primeira é a serifa que todo gerador escolhe. A segunda é ausência de voz. |
| Texto em gradiente | `bg-clip-text` + `text-transparent` | Ênfase vem de peso e tamanho. |
| Mesmo fade-in em toda seção | `transition: all`, `ease-in-out` em tudo, reveal idêntico repetido, três efeitos empilhados | Movimento sem propósito. Um site tem um momento autoral de movimento, não quinze. |
| Primeira dobra só texto | `hero` sem `img`, `video` ou `canvas` | A primeira dobra precisa de uma imagem forte de verdade. Também vale o contrário: hero lotado. |
| Placar de vaidade como prova | Contador `0 → 10.000`, `+50k seguidores`, `4.9★` sem fonte | Views, curtidas e seguidores não provam nada. Número só com fonte. |
| Ícone grosso de biblioteca, ou emoji no lugar de ícone | Lucide/FontAwesome em peso padrão espalhado; emoji em `h3` | Ícone é desenhado num traço só e num peso só, ou não existe. |
| Pessoa gerada por IA representando dono ou equipe | Foto de rosto sem origem; stock de aperto de mão | Pessoa real ou nenhuma. Foto real em alta, ou detalhe técnico anônimo, ou só texto e fatos. |
| Copy com cara de IA | Travessão, "em um mundo cada vez mais", "transforme", "eleve", "experiência única", "soluções inovadoras", tríade de adjetivos, "Saiba mais" | Texto que ninguém falaria em voz alta. |
| Tela travada no scroll | `pin: true`, trilho horizontal, canvas de frames, vídeo que segura a rolagem | Trava engasga no celular e irrita no desktop. Só com pedido explícito e teste aprovado. |
| Imagem ruim | `img` renderizada acima da resolução natural; foto baixada do Instagram em baixa; mapa cinza | Imagem em alta da fonte original ou nenhuma. Mapa colorido de verdade. |
| Botão chapado com glow | `box-shadow` colorido de raio zero em CTA | Halo sem offset é enfeite, não profundidade. |

Pra achar as pistas num projeto de uma vez:

```bash
rg -n -i "rounded-full|border-radius:\s*9+px|tracking-\[0\.[2-9]em\]|letter-spacing:\s*0?\.[2-9]em|grid-cols-4|from-purple|from-violet|#7c3aed|#a855f7|animate-pulse|bg-clip-text|transition:\s*all|Instrument Serif|Fraunces|Playfair|backdrop-blur|pin:\s*true" --glob '!node_modules' --glob '!*.lock'
```

A lista do detector é pista, não veredito. Um `rounded-full` num avatar não é vício. Um `backdrop-blur` em cima de um vídeo é o uso certo. Decida olhando o render, não o grep.

## 2. Decidir: o que entra no lugar

Cada vício tem uma troca. A troca segue a gramática editorial: simples e forte ganha de poluído e bonitinho.

- **Canto.** CTA e aba em canto reto. O botão se afirma pela área de clique e pelo verbo, não pelo raio.
- **Cor.** Uma cor tirada do ofício (do produto, da fachada, do material, da história) e um neutro quente. Nunca gradiente, nunca a cor da moda. Se o negócio não tem cor, escolha uma e sustente.
- **Hierarquia.** Diferença real de tamanho e peso entre níveis. O título fala sozinho; a legenda em cima dele sai. Teto de display em 7rem; tracking não passa de -0.03em.
- **Tipografia.** No máximo duas famílias e uma voz. Display com caráter próprio. Troca de fonte vai como proposta ao dono, nunca aplicada por conta.
- **Movimento.** Uma curva pro site inteiro, `cubic-bezier(.16, 1, .3, 1)`. Um momento autoral de movimento, com propósito que cabe numa frase. Reveal só com `transform` e `opacity`, entre 0.6s e 1s, escada de 0.08s. Scroll livre do primeiro segundo ao último.
- **Primeira dobra.** Quem é, o que faz, como falar, e uma imagem forte real. Nunca só texto, nunca lotada.
- **Prova.** Afirmação do que a marca sabe fazer, dita como afirmação. Foto real. Review real na íntegra, com nome. Número só com fonte visível.
- **Imagem.** Foto real em alta da fonte original (site do negócio, Google, imprensa). Se precisar gerar, gere cena ou objeto, nunca pessoa real.
- **Profundidade.** Camadas sobrepostas com intenção. Nunca bloco empilhado, nunca caixa dentro de caixa. Elevação declarada uma vez: borda ou sombra, não as duas.
- **Copy.** Sem travessão. Verbo que nomeia a ação no botão ("Chamar no WhatsApp", não "Saiba mais"). Nada de clichê. O que já existe fica como está.
- **O que você não desenhou.** Seleção de texto, scrollbar, anel de foco, caret e numerais tabulares vêm do navegador. Tematize a partir da paleta. Padrão do navegador nesses detalhes denuncia montagem.

Teto por rodada: dois mecanismos novos. Mais que isso quebra o site e quebra a lei zero.

## 3. Executar

- Cada vício encontrado é um item do lote, numerado, com o lugar exato. Execute um por um, na ordem, sem mexer no que não está no lote.
- Diff mínimo. Nada de reescrever arquivo inteiro pra trocar um raio.
- Item que depende de decisão do dono (fonte, texto, assinatura visual) fica marcado como proposta e não entra no diff.
- Relate item por item, na ordem do lote. Sem item aberto não existe "pronto".

## 4. Provar

Nada sai sem passar aqui, em desktop 1440 e celular 390:

- Screenshot antes e depois, lado a lado, nos dois tamanhos.
- Overflow horizontal zero.
- Zero erro de console.
- Todas as imagens carregando, nenhuma renderizada acima da resolução natural.
- Fontes declaradas carregadas.
- Elementos de reveal com opacidade final 1.
- Scroll livre do topo ao fim, sem intro, vídeo ou música travando.
- Cada aba, botão e link clicado: muda o que tem que mudar e volta.
- Inventário da lei zero conferido: nada que estava aprovado sumiu ou piorou.

## Saída

```
ACABAMENTO · <nome do projeto>

Ficou como estava
<inventário da lei zero, em uma linha por item>

Trocado, item por item
1. <vício> · <onde> · <o que entrou no lugar>
2. ...

Proposta separada (precisa do seu ok)
- Tipografia: <de → para, com o porquê>
- Texto: <trecho antes → trecho depois>

Prova
antes-1440.png · depois-1440.png · antes-390.png · depois-390.png
```

---

Feito pela Kore ID, Rio de Janeiro. As leis vêm das correções reais de quem revisa site feito com IA todo dia. MIT.
