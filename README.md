# mini-trator-
montagem do robo otto , pra estudo da materia de computaçao aplicada a engenharia
# 🚜 Trator Carregador Automatizado (Mini Loader) com Arduino Nano

Este projeto consiste na modelagem lógica e no desenvolvimento elétrico/firmware de um mini trator carregador robótico automatizado. O comportamento dinâmico do robô foi projetado utilizando o formalismo de **Redes de Petri** (Máquina de Estados) para garantir uma transição segura e previsível entre as etapas de operação.

O protótipo virtual foi montado e validado de ponta a ponta na plataforma de simulação eletrônica **Wokwi**.

---

## 🛠️ Especificações do Hardware (Modelagem Elétrica)

O chassi e os sistemas do trator utilizam os seguintes componentes eletrônicos:
*   **Microcontrolador:** Arduino Nano V3 (ATmega328P) — ideal para otimização de espaço.
*   **Visão/Sensores:** Sensor Ultrassônico HC-SR04 para detecção de obstáculos em tempo real.
*   **Mecanismo de Carga:** 2x Servo Motores convencionais para controle angular do Braço e da Caçamba.
*   **Sistema de Tração:** 2x Servo Motores de Rotação Contínua acoplados às rodas.
*   **Segurança Visual:** 1x LED Difuso (Indicador de marcha ré).
*   **Segurança Sonora:** 1x Buzzer Piezoelétrico (Sinalizador acústico de ré).

---

## ⚙️ Arquitetura de Estados (Baseado em Rede de Petri)

A lógica do firmware gerencia o trator de forma cíclica através de condições e eventos bem definidos:

1.  **BUSCANDO:** O trator avança em linha reta com a caçamba raspando rente ao chão procurando material.
2.  **CARREGANDO:** Ao atingir o tempo limite de busca, o trator reduz a velocidade, levanta os braços mecânicos e inclina a caçamba para trás para reter a carga.
3.  **TRANSPORTANDO:** O robô se desloca com a carga erguida até o destino final, onde realiza o tombo frontal da caçamba para descarregar e reiniciar o ciclo.
4.  **OBSTÁCULO DETECTADO (Interrupção de Emergência):** Caso o sensor ultrassônico detecte qualquer barreira a menos de **20 cm**, o fluxo normal é interrompido. O trator aciona a marcha ré enquanto executa alertas visuais (LED piscante) e sonoros (Buzzer intermitente) sincronizados. Após desviar do perigo, ele recalcula a rota.

---

## 🚀 Como Executar o Projeto

1. Clone este repositório no seu computador.
2. Acesse a plataforma [Wokwi](https://wokwi.com).
3. Crie um novo projeto utilizando a placa **Arduino Nano**.
4. Copie o conteúdo do arquivo `diagram.json` deste repositório e cole na aba de mesmo nome no simulador para gerar os componentes e fiação automaticamente.
5. Copie o código de `sketch.ino`, cole na aba principal do simulador e certifique-se de instalar a biblioteca `Servo.h` no gerenciador do Wokwi.
6. Clique em **Start Simulation** para assistir ao trator operando!

---
Desenvolvido como estudo de automação, modelagem estocástica/sistemas discretos e robótica embarcada.
