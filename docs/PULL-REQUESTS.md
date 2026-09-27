# Padrão de documentação para Pull Requests

Toda Pull Request explica contexto e comportamento. Alguém que não participou do desenvolvimento precisa entender, nesta ordem: contexto, objetivo, alterações, validação e relacionamentos.

O título no GitHub continua `MIND-123: descrição objetiva`. O corpo segue o template em `.github/pull_request_template.md`.

## Estrutura

```md
## 🚀 Pull Request: MIND-123 – título

📖 **História**

[Por que a alteração precisou ser feita.]

---

🎯 **Objetivo**

[O que a alteração pretende alcançar.]

---

🔧 **O que foi feito**

### [Área ou funcionalidade]

- [Alteração realizada]

---

🧪 **Testes e Verificações**

- [Validação realizada]

---

🧩 **Commits Principais**

- **[tipo(escopo):]**
  - [Resumo da alteração]

---

📎 **Relacionados**

- MIND-123 — [relação direta]
```

Omita **Relacionados** quando não houver tarefa, PR ou alteração anterior ligada a esta entrega.

## História

A História responde por que a alteração precisou existir. Não repita o título da issue.

Forma curta, em um ou dois parágrafos:

> Após [mudança ou contexto], foi necessário [ação] para [motivo ou resultado esperado].

## Objetivo

O Objetivo responde o que se quer resolver ou melhorar. Descreva o resultado, sem método, tabela ou nome de função.

Preferir: padronizar os dados iniciais do sistema com a nova nomenclatura.

## O que foi feito

Agrupe as alterações por contexto funcional ou técnico. Use subtítulo quando houver mais de uma área.

```md
### 💾 Banco de dados

- Atualizada a estrutura das categorias.
- Ajustados os relacionamentos com o instrumento publicado.

### ⚙️ Backend

- Ajustada a busca para devolver só os registros da pessoa autenticada.
```

Cada item começa com verbo de ação: criado, atualizado, corrigido, removido, substituído, renomeado, ajustado, adicionado, refatorado, padronizado.

Explique o comportamento. Detalhe de chamada interna só entra quando ele for necessário para entender a mudança.

## Testes e verificações

Registre como a alteração foi validada: teste automatizado, teste manual, endpoint, banco, seed, fluxo, comparação antes e depois, ou ambiente específico.

```md
- Confirmado que o fluxo de login conclui sem intervenção administrativa.
- Validado o retorno da faixa devolvida pela API.
- Verificada a integridade dos registros da pessoa autenticada.
```

Inclua imagem, vídeo, log ou resposta de API quando a mudança for de interface ou de contrato. Não afirme que algo foi testado se essa informação não existir na tarefa, no commit, no código ou na execução.

## Commits principais

Liste só os commits que explicam a entrega. O emoji já está na mensagem, no catálogo de [CONVENTIONS.md](CONVENTIONS.md). Na PR, mostre o tipo e o escopo:

```md
- **refactor(seed):**
  - Atualizar dados iniciais
  - Padronizar nomenclaturas
  - Remover dados obsoletos
```

Tipos usuais: `feat`, `fix`, `refactor`, `chore`, `docs`, `test`, `ci`, `perf`, `style`, `cleanup`, `remove`, `raw`.

## Relacionados

Aponte tarefa, PR ou alteração anterior com relação direta.

```md
- MIND-567 — Alteração da estrutura de categorias.
- MIND-569 — Atualização dos dados iniciais.
```

## Escrita

- Português, Markdown e emojis nas seções do template.
- Contexto e resultado primeiro; detalhe depois.
- Listas quando houver várias alterações; subtítulos para separar grupos.
- Texto curto. A mesma informação não se repete em História, Objetivo e O que foi feito.
- Sem dados inventados. Use só o que está na issue, nos commits, no código ou nos testes.

A PR descreve o que mudou e por que mudou. Ela não é o manual da implementação.
