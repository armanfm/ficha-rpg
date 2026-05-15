# Ficha RPG + Tracker de Sessão

Um arquivo HTML que você abre no navegador. Sem instalação, sem internet. O que você preencher fica salvo automaticamente no navegador e continua lá na próxima vez que abrir.

---

## As 3 abas

### 1. Ficha — preenche uma vez

Aqui você monta o personagem. Não mexe mais nisso durante o jogo.

**Nome** — campo editável no topo.

**Informações** — Clã, Geração, Natureza, Comportamento, Refúgio, Conceito, Jogador.

**Atributos** — clique nos pontos para definir o valor (1–5):
- Físicos: Força, Destreza, Vigor
- Social: Carisma, Manipulação, Aparência
- Mentais: Percepção, Inteligência, Raciocínio

**Habilidades** — pontos de 0 a 5:
- Talentos, Perícias, Conhecimentos
- Cada coluna tem um campo em branco no final para especializações livres

**Virtudes** — pontos em azul para diferenciar:
- Consciência / Convicção
- Autocontrole / Instinto
- Coragem

**Pools base:**
- Força de Vontade (define o máximo no tracker)
- Humanidade / Caminho
- Sangue máximo (define o tamanho da pool no tracker)

> Clique num ponto já marcado para diminuir o valor.

---

### 2. Disciplinas — configura uma vez

Aqui você cadastra seus poderes. Também não mexe durante o jogo — só na criação ou evolução do personagem.

**Adicionar disciplina:**
1. Clique em **+ Nova Disciplina**
2. Digite o nome
3. Defina o nível nos pontos (1–5)

**Adicionar poder:**
1. Clique em **+ Poder** na disciplina
2. Preencha:

| Campo | O que colocar |
|-------|--------------|
| Nome | Nome do poder |
| Nível | 1 a 5 |
| Descrição / Efeito | O que faz em jogo |
| **Atributo** | Qual atributo rola (ex: Manipulação) |
| **Habilidade** | Qual habilidade soma — opcional |
| Dificuldade | Número alvo dos dados |
| Custo Sangue | Pontos gastos ao ativar |
| Custo FdV | 0 ou 1 |
| Duração | Instantâneo / 1 Turno / 1 Cena / Permanente |
| Passivo | Sem rolagem, sempre ativo |

O sistema pega os valores de Atributo e Habilidade direto da Ficha na hora de calcular os dados. Você não precisa digitar nada na hora do jogo.

---

### 3. Combate — tracker dinâmico de sessão

Essa é a aba que fica aberta durante o jogo. Tudo aqui muda em tempo real.

#### Turno e Cena

- **− / + no Turno** — avança ou volta manualmente
- **⟶ Nova Cena** — ao clicar:
  - Turno volta pra 1
  - Boosts de atributo físico somem
  - Efeitos com duração "1 Cena" expiram
  - O registro mostra o que encerrou

#### Atributos Físicos — boost com sangue

Mostra o valor atual de Força, Destreza e Vigor. Para boostar:
- Clique **🩸 +1** — gasta 1 sangue e sobe o atributo em 1 até fim da cena
- O valor boosted fica em dourado
- Qualquer poder que use esse atributo recalcula os dados automaticamente
- **Somem ao virar a cena**

#### Efeitos Ativos

Lista os poderes que estão em vigor. Poderes de "1 Cena" aparecem aqui e saem automaticamente na virada. Você pode remover manualmente com **✕**.

#### Usando um Poder

Cada poder mostra o pool calculado em tempo real:
> *Manipulação 3 + Ocultismo 4 → 7 dados (Dif. 7)*

Clique em **Usar**:
1. Abre o painel com descrição e dados
2. **🎲 Rolar** — mostra os dados (verde = sucesso, cinza = falha, vermelho = 1)
3. **▶ Ativar** — gasta sangue/FdV, registra no log, marca o efeito como ativo

Se não tiver recursos suficientes, avisa antes de deixar ativar.

#### Pontos de Sangue

Pool visual de círculos. Clique num cheio para gastar, num vazio para recuperar. Ou usa os botões **− 1 / + 1**.

#### Vitalidade

Clique na caixinha de cada nível para ciclar o tipo de dano:

**Vazio → Contusão (/) → Letal (✕) → Agravado (*) → Vazio**

O status no topo atualiza sozinho.

#### Força de Vontade

- **Permanente** — valor definido na Ficha, não muda em jogo
- **Temporária** — o que sobrou, clique para gastar ou recuperar

#### Registro

Tudo que acontece vai pro log com cena e turno marcados. Limpe entre sessões.

---

## Fluxo de uso

```
Criação do personagem
  → Aba Ficha: preenche atributos e habilidades
  → Aba Disciplinas: cadastra poderes com atributo + habilidade + custo

Antes de cada sessão
  → Confirma se a ficha está certa
  → Vai pra aba Combate

Durante o jogo (tudo na aba Combate)
  → Usa poder → clica Ativar → sistema desconta recursos e rola
  → Toma dano → marca na Vitalidade
  → Gasta sangue pra boostar → botão 🩸 no atributo
  → Cena muda → clica Nova Cena → boosts e efeitos somem

Fim da sessão
  → Fecha o navegador
  → Ficha e disciplinas continuam salvas
  → Tracker de combate começa do zero na próxima sessão
```

---

## Sobre o save

Os dados ficam salvos no `localStorage` do navegador, vinculados ao arquivo. Isso significa:

- Funciona offline, sem conta, sem servidor
- Se abrir o arquivo em outro navegador ou outra máquina, começa vazio
- Para zerar: F12 → Application → Local Storage → `vtm2` → Delete
