# 🛰️ Software de Telemetria de Solo: Rumo a Cabo Canaveral

> ⚠️ **STATUS DO PROJETO:** Em desenvolvimento ativo (Fase de Modelagem de Arquitetura e Setup de Ambiente).

## 📝 Descrição do Projeto
Este repositório foi inicializado para hospedar a construção de um sistema híbrido de processamento e análise de telemetria de solo em tempo real para missões aeroespaciais. O objetivo do software é receber pacotes de dados brutos de satélite (dados binários e hexadecimais), realizar o parsing de alta performance, validar a integridade das informações estruturais e fornecer uma interface analítica para a equipe de controle de missão.

A arquitetura planejada divide o ecossistema em duas camadas estratégicas que estão sendo desenvolvidas:
1. **Engine Core (Linguagem C):** Camada em fase inicial de codificação, focada na captura de baixo nível, manipulação de bits (operações bitwise), decodificação de frames e verificação de integridade de dados sob restrições rígidas de tempo de execução.
2. **Analysis Interface (Python):** Camada de alto nível planejada para o tratamento assíncrono dos dados decodificados, geração de logs estruturados e interface analítica para monitoramento de telemetria crítica (altitude, velocidade, órbita e status dos subsistemas).

---

## 🛠️ Arquitetura e Fluxo de Dados Projetado

* **Camada 01: Ingestão de Dados (C) — *Em Progresso***
  * Manipulação de buffers e ponteiros para leitura de pacotes binários de telemetria.
  * Operações Bitwise para mascaramento e extração de flags de status dos sensores do satélite.
  * Validação de integridade de pacotes.

* **Camada 02: Pipeline de Comunicação — *A Implementar***
  * Exportação de dados estruturados e limpos a partir do Core em C para o interpretador Python via arquivos de log, sockets locais ou bindings.

* **Camada 03: Análise e Visualização (Python) — *A Implementar***
  * Parsing das estruturas tratadas.
  * Armazenamento e manipulação lógica de séries temporais de telemetria.
  * Preparação para renderização e logs analíticos de controle da missão.

---

## 🚀 Tecnologias Utilizadas

* **Linguagem C:** Escolhida pela eficiência máxima, controle preditivo de memória e manipulação cirúrgica de dados de hardware/baixo nível.
* **Python:** Utilizado pela agilidade no processamento de dados de alto nível, manipulação de arquivos assíncronos e ecossistema robusto para engenharia.
* **Ambiente de Desenvolvimento:** Projetado e testado sob o ecossistema **Fedora Linux**, utilizando virtualização KVM para simular condições e fluxos de dados de rede em ambientes isolados.

---

## 📁 Estrutura Inicial do Repositório

O esqueleto de diretórios foi estruturado para suportar o crescimento modular do código:

```text
├── core/
│   ├── include/        # Arquivos de cabeçalho (.h) [Planejado]
│   ├── src/            # Implementação do parser em C (.c) [Em desenvolvimento]
│   └── Makefile        # Script de compilação automatizada
├── analysis/
│   ├── parser.py       # Módulo Python de tratamento e análise [Planejado]
│   └── main.py         # Ponto de entrada da camada analítica [Planejado]
├── data/
│   └── telemetry_sim/  # Arquivos de simulação de pacotes binários
└── README.md
