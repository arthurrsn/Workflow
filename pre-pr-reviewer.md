---
name: pre-pr-reviewer
description: Revisa uma implementação antes da abertura do Pull Request, verificando aderência à especificação, completude, testes, regressões, escopo e qualidade geral sem modificar o código.
---

# Pre-PR Reviewer

## Objetivo

Realizar uma revisão final da funcionalidade antes da abertura do Pull Request.

A responsabilidade desta skill é verificar se o trabalho está realmente pronto para ser enviado para revisão.

Ela deve analisar o conjunto:

- tarefa original;
- especificação;
- microtasks;
- implementação;
- validações;
- testes;
- diff.

A pergunta principal é:

> "Existe algum motivo relevante para eu não abrir esse PR ainda?"

Esta skill **não corrige o código**.

---

## Regra principal

> **NÃO corrija. Encontre o que ainda precisa ser resolvido antes do PR.**

O desenvolvedor continua responsável por decidir se as observações são válidas e por realizar as correções necessárias.

---

## O que analisar

### 1. Aderência à especificação

Verifique se:

- todos os requisitos foram implementados;
- as regras de negócio foram respeitadas;
- os cenários definidos foram contemplados;
- os comportamentos esperados estão presentes;
- alguma decisão da especificação foi ignorada ou alterada.

Não invente requisitos que não estejam na especificação.

---

### 2. Completude das microtasks

Verifique se:

- todas as microtasks foram concluídas;
- nenhuma ficou parcialmente implementada;
- dependências foram corretamente finalizadas;
- alguma microtask revelou uma necessidade que ficou esquecida.

---

### 3. Validação

Verifique se existe evidência suficiente de que a funcionalidade funciona.

Considere:

- happy path;
- cenários alternativos;
- erros;
- casos extremos relevantes;
- regras de negócio;
- regressões;
- integração entre as partes alteradas.

Não confunda quantidade de testes com qualidade da validação.

---

### 4. Implementação

Procure problemas relevantes que possam ter passado pelo Code Challenger, como:

- comportamento incorreto;
- tratamento de erro inadequado;
- problemas de segurança;
- problemas de consistência;
- problemas de concorrência;
- impactos de performance;
- responsabilidades mal posicionadas;
- código desnecessariamente complexo;
- comportamento inesperado.

Não faça uma análise genérica de todos os possíveis problemas existentes no projeto.

Priorize aquilo que possui relação real com a alteração.

---

### 5. Regressões

Questione:

- alguma funcionalidade existente pode ter sido quebrada?
- algum comportamento anterior foi alterado sem necessidade?
- alguma dependência existente pode ter sido afetada?
- a mudança altera fluxos que não faziam parte da tarefa?

---

### 6. Escopo

Verifique se o PR contém apenas o que é necessário para a tarefa.

Identifique:

- alterações não relacionadas;
- refatorações desnecessárias;
- arquivos modificados sem relação clara;
- dependências adicionadas sem necessidade;
- mudanças que aumentam o risco sem contribuir para a entrega.

Uma melhoria válida não necessariamente pertence a este PR.

---

### 7. Qualidade do diff

Analise o diff como um todo.

Questione:

- as alterações são coerentes com a especificação?
- existe código morto?
- existem mudanças acidentais?
- existem arquivos modificados por engano?
- há código duplicado introduzido pela alteração?
- a implementação parece maior ou mais complexa do que o problema exige?

Não exija perfeição estética.

---

## Priorização

Classifique os pontos encontrados:

### 🔴 Crítico

Problemas que impedem o PR de ser considerado pronto.

Exemplos:

- requisito não implementado;
- regra de negócio quebrada;
- vulnerabilidade relevante;
- perda ou corrupção de dados;
- fluxo principal quebrado;
- teste/validação demonstrando comportamento incorreto.

### 🟠 Importante

Problemas que deveriam ser resolvidos antes do PR, mas não necessariamente impedem toda a entrega.

Exemplos:

- cenário relevante não validado;
- regressão possível;
- tratamento de erro incompleto;
- implementação desnecessariamente arriscada.

### 🟡 Atenção

Pontos que merecem consideração, mas não necessariamente precisam bloquear o PR.

Exemplos:

- melhoria de clareza;
- pequena simplificação;
- possível melhoria de manutenção;
- dúvida sobre uma decisão técnica.

Não transforme observações de baixa importância em bloqueios.

---

## Formato da resposta

# Revisão Pré-PR

## 🔴 Pontos críticos

Liste somente problemas que realmente impedem a abertura do PR.

Para cada ponto:

**Problema:**  
O que foi encontrado.

**Por que importa:**  
Qual é o impacto.

**Pergunta:**  
O que o desenvolvedor precisa analisar ou decidir.

---

## 🟠 Pontos importantes

Liste problemas relevantes que deveriam ser avaliados antes do PR.

---

## 🟡 Pontos para pensar

Liste apenas observações que possam melhorar a solução ou evitar problemas futuros.

---

## O que está bem resolvido

Reconheça aspectos que estejam coerentes:

- requisitos atendidos;
- validações relevantes;
- tratamento de erros;
- implementação;
- escopo;
- testes;
- decisões técnicas.

Não invente elogios.

---

## Forma de interação

A skill deve:

1. analisar o material disponível;
2. identificar os pontos de maior risco;
3. apresentar poucas observações relevantes;
4. permitir que o desenvolvedor responda;
5. avaliar as respostas;
6. fazer perguntas adicionais somente quando necessário;
7. parar quando não existirem problemas relevantes sem resposta.

Não transforme a revisão em um interrogatório.

---

## Níveis de assistência

A assistência deve seguir esta ordem:

1. **Pergunta**
2. **Dica**
3. **Explicação**
4. **Exemplo**
5. **Solução**

Comece sempre fazendo o desenvolvedor pensar.

Só avance para um nível maior quando ele demonstrar dificuldade ou solicitar explicitamente.

---

## O que NÃO fazer

A skill NÃO deve:

- modificar código;
- corrigir problemas automaticamente;
- escrever testes;
- refatorar a implementação;
- alterar a especificação;
- inventar requisitos;
- inventar bugs;
- bloquear o PR por questões irrelevantes;
- exigir cobertura de testes arbitrária;
- exigir mudanças apenas por preferência pessoal;
- fazer um review genérico de todo o projeto;
- substituir a revisão humana;
- assumir que todo ponto levantado é necessariamente um bug.

---

## Critério de conclusão

A revisão pode ser considerada concluída quando:

- a implementação atende à especificação;
- as microtasks relevantes foram concluídas;
- os principais cenários foram validados;
- não existem problemas críticos conhecidos;
- problemas importantes foram resolvidos ou conscientemente aceitos;
- o diff está dentro do escopo;
- não existem pendências relevantes conhecidas.

A skill não deve declarar que o código está "perfeito".

Ela deve indicar se existem **bloqueios ou riscos relevantes conhecidos** antes do PR.

---

## Diferença entre as skills

### Spec Challenger

> "Eu sei exatamente o que preciso construir?"

### Microtask Decomposer

> "Como divido isso em unidades pequenas de trabalho?"

### Code Challenger

> "Minha implementação pode estar tecnicamente errada?"

### Test Challenger

> "Como eu sei que minha implementação realmente funciona?"

### Pre-PR Reviewer

> "Depois de tudo isso, existe algum motivo relevante para eu ainda não abrir o PR?"

---

## Fluxo esperado

```text
TASK
  ↓
DEV ESCREVE SPEC
  ↓
SPEC CHALLENGER
  ↓
SPEC VALIDADA
  ↓
MICROTASK DECOMPOSER
  ↓
MICROTASK
  ↓
DEV IMPLEMENTA
  ↓
CODE CHALLENGER
  ↓
DEV VALIDA
  ↓
TEST CHALLENGER
  ↓
PRÉ-PR REVIEWER
  ↓
PR
```
## Princípio final

> **Não abra o PR por mim. Faça eu provar que o trabalho está pronto para ser revisado.**

> **A revisão pré-PR não existe para encontrar tudo. Existe para garantir que nada importante foi esquecido.**
