# Projeto: Robô Seguidor de Linha

## Objetivo

Programar um robô capaz de identificar uma linha no chão e segui-la de forma automática utilizando sensores infravermelhos e motores.

---

## Como funciona?

O robô possui sensores na parte inferior que identificam a diferença entre superfícies claras e escuras.

* Linha preta → Sensor detecta a linha.
* Fundo branco → Sensor não detecta a linha.

Com base nessas leituras, o programa decide para qual lado o robô deve se mover.

---

## Regras de Funcionamento

### Linha no centro

Se a linha estiver centralizada nos sensores:

→ O robô segue em frente.

### Linha à esquerda

Se a linha for detectada pelos sensores da esquerda:

→ O robô vira para a esquerda.

### Linha à direita

Se a linha for detectada pelos sensores da direita:

→ O robô vira para a direita.

### Linha perdida

Se nenhum sensor detectar a linha:

→ O robô para ou procura a linha novamente.

---

## Componentes Utilizados

* Microcontrolador
* Sensores de linha (IR)
* Motores DC
* Ponte H
* Chassi do robô
* Bateria
* Cabos de conexão

---

## Fluxograma Simplificado

Iniciar

↓

Ler sensores

↓

Linha encontrada?

├─ Sim → Corrigir direção

└─ Não → Parar

↓

Repetir processo

---

## Desafio

Após concluir a programação básica:

1. Aumente a velocidade do robô.
2. Faça curvas mais suaves.
3. Adicione um LED indicando quando a linha foi encontrada.
4. Tente fazer o robô completar uma pista sem sair da linha.

---

## Aprendizados Esperados

Ao final desta atividade você deverá compreender:

* Leitura de sensores.
* Estruturas condicionais (if/else).
* Controle de motores.
* Tomada de decisão em sistemas embarcados.
* Conceitos básicos de robótica móvel.

Boa programação!
