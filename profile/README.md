# Sistema de Controle e Despacho de Ocorrências (Bombeiros)
 
Este repositório contém a especificação de requisitos e a arquitetura inicial para um sistema interno de despacho e controle operacional (**CAD - Computer-Aided Dispatch**) voltado para o corpo de bombeiros. O sistema foi projetado para centralizar o atendimento de chamados, a gestão de frotas de veículos emergenciais, o controle de bases físicas e o monitoramento geoespacial em tempo real.
 
---
 
## 1. Propósito do Sistema
 
O objetivo principal do sistema é otimizar o tempo de resposta a emergências e centralizar a gestão operacional das forças de resgate. Ele atua como uma ferramenta interna para a central de operações (ex: 193), permitindo que os operadores recebam chamados telefônicos, realizem a triagem das ocorrências, gerenciem a frota de veículos disponíveis e façam o despacho inteligente de recursos com base na proximidade e na gravidade do incidente.
 
---
 
## 2. Usuários do Sistema
 
* **Operadores da Base / Central de Operações:** Responsáveis por receber as ligações de emergência, registrar as informações essenciais da ocorrência no sistema, realizar a triagem de prioridade e despachar as viaturas adequadas para o local.
* **Guarnições / Bombeiros nas Viaturas:** Responsáveis por operar os veículos de atendimento. Eles interagem com o sistema para atualizar o status operacional da viatura (em deslocamento, no local, disponível) e preencher relatórios técnicos pós-atendimento.
 
---
 
## 3. Arquitetura de Entidades Principais
 
O sistema foi estruturado com base em quatro pilares fundamentais de dados interconectados:
1.  **Bases:** Representa as unidades físicas (quartéis) e centrais de comando.
2.  **Ocorrências:** Representa os incidentes e chamados de socorro ativos ou encerrados.
3.  **Veículos:** Representa a frota operacional de viaturas especializadas.
4.  **Mapa:** Interface geográfica responsável pelo rastreamento e cálculo de rotas em tempo real.
 
---
 
## 4. Requisitos Funcionais (RF)
 
### Módulo 1: Base & Central de Operações
* **RF01 - Cadastro de Bases/Quartéis:** O sistema deve permitir o cadastro de múltiplas bases físicas, definindo sua localização geográfica exata e sua respectiva área de jurisdição operacional.
* **RF02 - Atendimento de Chamados:** O sistema deve fornecer uma interface de entrada rápida para que o operador registre os dados essenciais coletados via telefone (nome do solicitante, contato, descrição da emergência).
* **RF03 - Busca Rápida de Endereços:** O sistema deve integrar um validador de endereços ágil para localizar cruzamentos, ruas e bairros em tempo real durante o preenchimento do chamado.
* **RF04 - Painel de Despacho (Fila/Kanban):** O sistema deve exibir uma tela consolidada listando as ocorrências aguardando atendimento de forma visual, organizadas por prioridade.
 
### Módulo 2: Gestão de Ocorrências
* **RF05 - Ciclo de Vida da Ocorrência:** O sistema deve permitir a criação, edição, visualização e o encerramento formal de registros de ocorrência pelos operadores autorizados.
* **RF06 - Triagem e Priorização:** O sistema deve classificar automaticamente ou manualmente o nível de gravidade e o tipo de ocorrência (ex: Incêndio Estrutural, Resgate Veicular, Atendimento Pré-Hospitalar - APH).
* **RF07 - Despacho de Viaturas:** O sistema deve sugerir e permitir a vinculação de veículos específicos a uma ocorrência com base na natureza do chamado (ex: enviar uma ambulância para acidentes com vítimas ou caminhão Auto Bomba para incêndios).
 
### Módulo 3: Frota de Veículos (Viaturas)
* **RF08 - Cadastro de Frota:** O sistema deve permitir o registro detalhado de todas as viaturas, armazenando informações como tipo (ABTR, ASU, Auto Escada), placa, prefixo de rádio e capacidades técnicas.
* **RF09 - Controle de Status Operacional:** O sistema deve permitir a atualização e visualização em tempo real do estado de cada viatura (ex: "Disponível na Base", "Em Deslocamento", "No Local", "Em Manutenção").
* **RF10 - Gestão de Guarnição:** O sistema deve permitir associar quais bombeiros e comandantes estão alocados em cada viatura durante um turno de serviço específico.
* **RF11 - Controle de Insumos e Suprimentos:** O sistema deve permitir o registro rápido do status de materiais críticos pós-atendimento (ex: nível de água no tanque, cilindros de oxigênio utilizados, combustível).
 
### Módulo 4: Geolocalização & Mapa
* **RF12 - Mapa Interativo em Tempo Real:** O mapa deve plotar e atualizar dinamicamente a localização geográfica de todas as ocorrências ativas e das bases físicas cadastradas.
* **RF13 - Rastreamento da Frota:** O sistema deve rastrear os veículos em movimento via GPS, diferenciando-os na interface do mapa por ícones de acordo com a categoria e por cores de acordo com o status operacional.
* **RF14 - Cálculo e Sugestão de Rotas:** O sistema deve calcular a rota mais rápida entre a posição atual da viatura despachada (ou da base de origem) e o ponto exato da ocorrência geográfica mapeada.
