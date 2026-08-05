# Órbita Digital — site + status dos agentes

Este repositório hospeda o site institucional (`index.html`) e a "Sala dos
Agentes" (`agentes.html`), que lê `status.json` para mostrar quais agentes
estão ativos e o que cada um está fazendo.

## Regra permanente: todo agente reporta status

Sempre que um agente (Routine/trigger) da Órbita Digital estiver **ativo**
(enabled), ele precisa, ao final de cada ciclo, atualizar sua entrada em
`status.json` neste repo:

- `updated_at`: horário ISO 8601 UTC do ciclo que acabou de rodar.
- A entrada do agente (`id` correspondente): manter `"status":"ativo"` e
  escrever um `caption` curto e honesto do que foi feito nesse ciclo (ou do
  que está fazendo, se for algo mais longo) — sem prometer nada que não
  aconteceu de verdade.
- Se o agente for pausado pelo dono, mudar `"status":"pausado"` e deixar o
  `caption` explicando o último trabalho feito e por que está pausado.
- Nunca mexer nas entradas de outros agentes.
- Sempre commitar + dar push (branch `main`) depois de editar `status.json`.

Isso vale para **qualquer agente novo criado no futuro** para a Órbita
Digital, não só os que já existem — ao criar um agente novo, adicione uma
entrada correspondente em `status.json` e inclua o passo de atualização de
status nas instruções (prompt) do agente.

## Por que isso existe

O dono quer poder abrir `agentes.html` a qualquer momento e ver, tipo uma
sala de reunião, quais agentes estão rodando e o que cada um fez por último
— sem precisar perguntar no chat. `status.json` é a fonte da verdade dessa
página; ela só mostra o que os próprios agentes escreveram lá.
