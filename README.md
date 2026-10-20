# Acabamento

Seis skills que tiram a cara de amador de qualquer projeto feito com IA. Cinco existem, são de quem entende e já foram instaladas centenas de milhares de vezes. A sexta eu escrevi, e mora aqui.

Skill é um arquivo de instruções que o seu agente de código (Claude Code, Cursor, Codex, o que você usar) lê antes de trabalhar. Instala com um comando, e pronto: ele passa a trabalhar com a régua de quem fez a skill.

## Instalar tudo de uma vez

```bash
npx skills add vercel-labs/agent-skills --skill web-design-guidelines
npx skills add pbakaus/impeccable --skill impeccable
npx skills add pbakaus/impeccable --skill clarify
npx skills add emilkowalski/skills --skill improve-animations
npx skills add anthropics/skills --skill frontend-design
npx skills add emilkowalski/skills --skill prototype
npx skills add zTelerados/acabamento
```

Cada comando pergunta em qual agente instalar. Só isso.

## As seis

### 1. web-design-guidelines, da Vercel

A Vercel é a empresa por trás do Next.js. Essa skill pega o seu código e confere contra a régua de interface que eles usam dentro de casa: botão que não dá pra clicar no celular, texto sem contraste, foco de teclado que some, animação que trava. Devolve a lista com o arquivo e a linha de cada erro.

Mais de 750 mil instalações.

```bash
npx skills add vercel-labs/agent-skills --skill web-design-guidelines
```

### 2. impeccable, do Paul Bakaus

Paul Bakaus é ex-Google. A impeccable é polimento de verdade: ela sabe exatamente o que faz um site parecer feito por IA (rótulo em cima do título, passo 01 02 03, grid de card igual, texto em gradiente) e tira. Vem com a clarify, que reescreve texto de robô: mensagem de erro que ninguém entende, botão "Enviar", "Saiba mais".

Mais de 340 mil instalações.

```bash
npx skills add pbakaus/impeccable --skill impeccable
npx skills add pbakaus/impeccable --skill clarify
```

### 3. improve-animations, do Emil Kowalski

Emil Kowalski é o cara por trás do Sonner e do Vaul, as bibliotecas de toast e de gaveta que você já viu em todo app moderno. Essa skill varre todo movimento do seu projeto e devolve o que está errado, com o número da linha: a curva que faz o menu parecer lento, o botão que não responde ao toque, a animação que roda no lugar errado. Ela não mexe no código. Entrega o plano e você (ou o agente) executa.

Mais de 200 mil instalações.

```bash
npx skills add emilkowalski/skills --skill improve-animations
```

### 4. frontend-design, da Anthropic

A skill oficial de design da própria Anthropic. Ela lista os vícios que denunciam página gerada: uma palavra do título em itálico, rótulo em caixa alta, 01 02 03 em tudo, o mesmo fade em toda seção, creme com terracota. E manda o agente decidir antes de desenhar.

Mais de um milhão de instalações.

```bash
npx skills add anthropics/skills --skill frontend-design
```

### 5. prototype, do Emil Kowalski

Você descreve uma peça (um botão, um card de preço, um aviso) e ela constrói três versões de verdade diferentes, não três tons da mesma. Põe as três atrás de um seletor, você folheia ao vivo, aponta a que ficou certa, e ela sobe só aquela pro projeto. Amador aceita a primeira que a IA cospe. Profissional escolhe.

Mais de 150 mil instalações.

```bash
npx skills add emilkowalski/skills --skill prototype
```

### 6. acabamento, a bônus

Essa não existia, então eu escrevi. Ela recebe uma interface pronta e devolve a mesma interface sem os vícios de cara de IA: 19 vícios catalogados, com a pista de cada um no código e o que entra no lugar. Botão redondinho vira canto reto. Gradiente roxo vira uma cor tirada do negócio. Placar de vaidade vira prova com fonte. Texto de robô vira proposta pra você aprovar.

A lei acima de todas: não piora. Ela lista o que já está bom antes de tocar em qualquer coisa, muda só o que caiu numa lei, e só diz "pronto" com print de antes e depois no desktop e no celular.

As leis saíram de 973 correções em 150 conversas de site e código. Cada linha é um erro que se repetiu até virar regra.

```bash
npx skills add zTelerados/acabamento
```

Depois, no agente: "faz o acabamento desse projeto" ou "tira a cara de IA disso".

## Créditos

web-design-guidelines (Vercel Labs, MIT), impeccable e clarify (Paul Bakaus, MIT), improve-animations e prototype (Emil Kowalski, MIT), frontend-design (Anthropic). Os números de instalação são do skills.sh em 19/10/2026.

acabamento é da Kore ID, Rio de Janeiro. MIT.
