# Atividade 4 — Ambiente Hierárquico de Rede Local

## Identificação

**Curso:** Superior de Tecnologia em Redes de Computadores
**Disciplina:** Comutação de Redes Locais
**Atividade:** Avaliação 04 — Prática de Simulação de Ambiente Hierárquico
**Aluno(a):** Érica Rodrigues da Silva
**Ferramenta utilizada:** Cisco Packet Tracer

## Sobre o projeto

Esta atividade consiste em montar, dentro do Packet Tracer, uma rede local organizada em três camadas (núcleo, distribuição e acesso), com um roteador no topo da hierarquia. O trabalho envolve apenas a configuração física inicial do cenário, sem exigência de configurações lógicas neste momento. Como ponto extra, foi realizado também o endereçamento IP dos dispositivos finais, com teste de comunicação via ping.

## Topologia da rede

<img width="554" height="411" alt="image" src="https://github.com/user-attachments/assets/ec7e1a8f-cb98-4313-bedf-3b033980c7f5" />


## Equipamentos da rede

| Camada | Quantidade | Modelo | Nome |
|---|---|---|---|
| Roteamento | 1 | Router 2811 | Router1 |
| Núcleo | 2 | Switch multicamada 3560-24PS | Core 1, Core 2 |
| Distribuição | 2 | Switch multicamada 3560-24PS | Dist 1, Dist 2 |
| Acesso | 4 | Switch 2960-24TT | Acesso 1 a Acesso 4 |
| Desktops | 4 | PC-PT | PC0 a PC3 |
| Notebooks | 4 | Laptop-PT | Laptop0 a Laptop3 |
| Servidor | 1 | Server-PT | Server0 |

## Cabeamento

### Roteador → Núcleo

- Router1 (Fa0/0) ↔ Core 1
- Router1 (Fa0/1) ↔ Core 2
- Cabo: par metálico (cobre)

### Núcleo → Núcleo

Entre Core 1 e Core 2 existe mais de uma ligação física, usando portas GigabitEthernet. Essa estrutura já está pronta para uma futura,  configuração de EtherChannel, somando **4 Gbps**.
- CORE0 Gi1/0/2↔CORE1 Gi1/0/2
- CORE0 Gi1/0/3↔CORE1 Gi1/0/3
- CORE0 Gi1/0/4↔CORE1 Gi1/0/4
- CORE0 Gi1/0/5↔CORE1 Gi1/0/5
### Capacidade: 4 × 1 Gbps = 4 Gbps agregados quando o EtherChannel for ativado.

### Núcleo → Distribuição

- Core 1 ↔ Dist 1
- Core 1 ↔ Dist 2
- Core 2 ↔ Dist 1
- Core 2 ↔ Dist 2

Meio físico: fibra óptica monomodo (Single Mode Fiber), com mais de um cabo por par, preparando cada ligação para uma futura agregação de **2 Gbps**.

### Distribuição → Acesso

- Dist 1 ↔ Acesso 1
- Dist 1 ↔ Acesso 2
- Dist 2 ↔ Acesso 3
- Dist 2 ↔ Acesso 4

Todos utilizando **Cobre Straight-Through** .

### Acesso → Anfitriões

- Acesso 1 → PC0 e Laptop0
- Acesso 2 → PC1 e Laptop1
- Acesso 3 → PC2 e Laptop2
- Acesso 4 → PC3, Laptop3 e Server0

## Configurações realizadas

A atividade foi realizada principalmente na parte física da rede.

Não foram aplicadas configurações de:

- VLAN
- Rotamento
- EtherChannel
  
As interfaces conectadas foram habilitadas utilizando no shutdown.

Foram inseridos os módulos de fibra GLC-LH-SMD nos equipamentos correspondentes.

<img width="693" height="703" alt="image" src="https://github.com/user-attachments/assets/940b5449-a4b4-4508-b527-461eb19e23c5" />


## Endereçamento IP — Configuração extra

| Dispositivo | Endereço IP | Máscara |
|---|---|---|
| PC0 | 192.168.1.1 | 255.255.255.0 |
| Laptop0 | 192.168.1.2 | 255.255.255.0 |
| PC1 | 192.168.1.3 | 255.255.255.0 |
| Laptop1 | 192.168.1.4 | 255.255.255.0 |
| PC2 | 192.168.1.5 | 255.255.255.0 |
| Laptop2 | 192.168.1.6 | 255.255.255.0 |
| PC3 | 192.168.1.7 | 255.255.255.0 |
| Laptop3 | 192.168.1.8 | 255.255.255.0 |
| Server0 | 192.168.1.9 | 255.255.255.0 |

**PC0**


<img width="692" height="627" alt="image" src="https://github.com/user-attachments/assets/df3e15e2-c6ea-4f3d-9749-87fe1166f6c7" />


**Laptop0**


<img width="696" height="417" alt="image" src="https://github.com/user-attachments/assets/91d08691-7229-4aca-b338-d57081da93c1" />


**PC1**


<img width="699" height="435" alt="image" src="https://github.com/user-attachments/assets/32a6f51d-735a-411a-9fcd-8ffe372d58a3" />


**Laptop1**    


<img width="696" height="426" alt="image" src="https://github.com/user-attachments/assets/12bc8fea-1d68-42cd-ab24-a25c673eb706" />


**PC2**


<img width="691" height="458" alt="image" src="https://github.com/user-attachments/assets/05620ef7-933e-4c2c-8b08-bad80be33183" />


**Laptop2**


<img width="695" height="421" alt="image" src="https://github.com/user-attachments/assets/ccafe666-cd7a-45c2-acf9-1632cacf012a" />


**PC3**


<img width="698" height="434" alt="image" src="https://github.com/user-attachments/assets/480f9ffe-036a-49d3-bb14-907479326bd4" />


**Laptop3**


<img width="682" height="447" alt="image" src="https://github.com/user-attachments/assets/d198d3fb-f9f9-4c89-9470-cb43e387a080" />


**Server0**


<img width="692" height="414" alt="image" src="https://github.com/user-attachments/assets/d56021c4-cab0-4b33-80ce-18a50755e1df" />


Após a configuração dos endereços IP, foram realizados testes utilizando o comando ping para verificar a comunicação entre os dispositivos.
``


**PC1**


<img width="699" height="707" alt="image" src="https://github.com/user-attachments/assets/4d2d3946-9fa9-44ee-9f9a-c3451a34348a" />
<img width="691" height="704" alt="image" src="https://github.com/user-attachments/assets/564bc1a6-2d41-496b-908f-7d23d1eb80d1" />
<img width="694" height="712" alt="image" src="https://github.com/user-attachments/assets/33cbc983-4ae7-4d6b-9761-673a0e45c308" />




**Serve0**


<img width="687" height="703" alt="image" src="https://github.com/user-attachments/assets/4c4d035c-f3ec-4d11-9523-f794148221c6" />
<img width="695" height="712" alt="image" src="https://github.com/user-attachments/assets/54f47721-1642-4c0c-8555-fd709908ea00" />
<img width="701" height="709" alt="image" src="https://github.com/user-attachments/assets/cba7cb46-3f8c-443f-a435-ab764af3eb12" />
<img width="690" height="705" alt="image" src="https://github.com/user-attachments/assets/9cf88cff-46e6-4351-a947-81209830230c" />



A comunicação foi validada com o comando ping entre os dispositivos finais. Todos os PCs e Laptops conseguiram se comunicar com sucesso entre si e com o servidor.



