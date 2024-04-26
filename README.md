# AZR
# 1 - Computação em Nuvem

* Entrega de serviços de computação pela internet
* Computação, armazenamento, banco de dados, Machine Learning e IA
* Permite expansão rápida de recursos

## Responsabilidade Compartilhada

* Provedor: segurança física, energia, resfriamento, conectividade e SO 
* Cliente: dados e permissões
* Depende do tipo de serviços
  * On premises: total do cliente
  * Infra as a Service: parte física com o provedor
  * Plataform as a Service: parte física + SO com o provedor
  * Software as a Service: somente os dados e pérmissões com o cliente

## Modelos de Nuvem

* **Privada:** entrega de serviços pela internet dedicados somente a uma empresa (e gerenciada pela própria empresa ou terceiro)
* **Pública:** provedores (AWS, GCP, AZR) fornecem o serviço a quem queira comprar
* **Híbrida:** mescla de recursos
* **Várias Nuvens:** uso de múltiplos provedores, por diferentes recursos ou por transição
* **Azure Arc:** serviço de gerenciamento, permite várias nuvens
* **VMWare no Azure:** migração e gerenciamento de ambiente VMWare local para nuvem

## Consumo

* **CapEx:** despezas de capital
  * prédio, hardware
* **OpEx:** despezas de operações
  * assinatura de seviços, aluguéis, serviços em nuvem
* Vantagens da nuvem:
  * sem custos prévios
  * não é necessário prever necessidade de recursos
  * sem responsabilidade de manter estrutura física
  * flexibilidade para aumentar recursos
  * flexibilidade para reduzir custos desativando serviços

# 2 - Benefícios da Nuvem

* **Alta Disponibilidade:** medida em % de up time (SLA)
  * 99% ~> 7.2h por mês de downtime
  * 99.9% ~> 43min por mês de downtime
  * 99.95%
  * 99.99%
  * cada serviço tem um SLA diferente
* **Escalabilidade:** responder a picos de demanda
  * reduzir recursos em períodos de baixa demanda ~> redução de custos
  * **vertical:** alterar a capacidade de um recurso (CPU e RAM)
  * **horizontal:** alterar a quantidade de recursos (automático ou manual)
* **Confiabilidade:** distribuição global
  * garantia em caso de falhas regionais
  * resiliência: capacidade de se recuperar de falhas
* **Previsibilidade:** de desempenho e custos
  * desempenho: balanceamento de carga e dimensionamento automático
  * custos: monitoramento e análise de dados
* **Governança e Conformidade:** modelos de conjunto e auditoria
* **Segurança:** prevenção automática de DDoS
* **Gerenciamento:** controle dos recursos e formas de controlar
  * controle: escalar automaticamente, monitorar...
  * formas: web, cli, APIs e PowerShell

# 3 - Serviços

## Infrastructure as a Service 

* provedor é responsável  por manter o hardware, conectividade e segurança física
* usuário é reponsável por todo o resto, desde a instalação do SO
* basicamente um aluguel de hardware na nuvem
* **cenários:** migração lift-and-shift de on premises para cloud e ambientes de teste

## Plataform as a Service

* provedor é responsável pela instalação, licenciamento e manutenção do SO, banco de dados e ferramentas de desenvolvimento
* semelhante a um computador no domínio: o departamento de TI (provedor) cuida das atualizações e SO
* Banco de Dados SQL
* **cenários:** estrutura de desenvolvimento e Análise de Dados (BI)

## Software as a Service

* provedor é responsável por todo o ambiente
* usuário é responsável somente pelos dados, dispositivos e permissões
* **cenários:** softwares de emails, mensagens e finanças

# 4 - Arquitetura

* +100 serviços
  * 25 always free
  * vários 12 meses free
  * **área restrita:** disponibiliçao temporária de recursos para aprendizado no Microsoft Learn
* conta ~> assinaturas ~> grupos de recursos ~> recursos
* **Zonas de Disponibilidade**
  * datacenters separados dentro de uma região
  * independentes
  * conectados por fibra óptica de alta velocidade
  * serviços que dão suporte:
    * serviços fixados em uma zona
    * serviços com redundância de zona
    * serviços não regionais

* **Região**
  * 3 ou mais zonas de disponibilidade
    * algumas regiões não dão suporte a Zonas de Disponibilidade
  * alguns serviços são regionais
* **Pares de Regiões**
  * duplicação de conteúdo
  * regiões a 300 milhas de distância
  * alguns serviços não dão suporte
  * em caso de interrupção ampla, uma região de cada par é priorizada para restauração da disponibilidade
  * os dados residem na mesma geografia para fins de legislação
    * com exceção ao sul do Brasil

  * **Regiões Soberanas:** instâncias isoladas da instância principal do Azure (US Gov Virginia e Leste China)

* **Recursos e Grupos**
  * todo serviço é um recurso
  * todo recurso está em um grupo de recursos
  * um recurso pode ser movido de um grupo para outro
  * aplicar regras a um grupo **~>** aplica a todos os recursos do grupo
  * excluir um grupo exclui os recursos dele
  * não podem ser aninhados

* **Assinaturas**
  * gerenciamento de recursos, acesso e cobrança
  * limite por cobrança ou limite por controle de acesso
  * separar acesso a recursos por departamentos
  * separar ambiente de desenvolvimento e teste

* **Grupos de Gerenciamentos**
  * grupos de assinaturas
  * aplicar regras ao grupo **~>** aplica a todas as assinaturas
  * grupos de gerenciamento podem ser aninhados em até 6 níveis

# 5 - Computação e Rede

## Máquinas Virtuais

* IaaS
* ideal para configurações personalizadas de hospedagem
* VM do zero ou imagens de VM pré-configuradas
* **lift-and-shift:** criar uma imagem do servidor físico e subir em uma VM
* **Extensão de Script Personalizada:** script para execução/instalação em uma  VM em funcionamento

## Conjuntos de Escala de VM

* criar, monitorar e gerenciar grupo de VMs
* VMs idênticas com balanceamento de carga
* configurar resposta automática por demanda ou por agendamento

## Conjuntos de Disponibilidade de VM

* prevenção à indisponibilidade
* sem custo adicional
* por domínio de atualização e domínio de falha
* **atualização:** grupo de VMs que podem reiniciar ao mesmo tempo
* **falha:** grupo de VMs por origem de energia e rede

## Área de Trabalho Virtual

* qualquer dispositivo ou via browser
* usuários remotos
* protege dados da empresa (arquivos não são salvos localmente)
* **RBAC:** controle de acesso baseado em função
* sessão única ou várias sessões (vários usuários na mesma VM)

## Contêineres

* PasS
* instâncias de contêiner
* aplicativos de contêiner: permite balanceamento de carga
* Azure Kubernetes Service

## Funções

* serverless
* execução em resposta a um evento (geralmente solicitações REST)
* execução limitada a segundos
* dimensionadas automaticamente a partir da demanda
* sem estado (padrão) ou com estado (acompanhar atividade anterior)

## Hospedagem de Aplicativo

* hospedagem de aplicativo sem se preocupar com a infra
* compatível com Windows e Linux
* compatível com Azure DevOps, repositórios Git e pipelines
* serviço HTTP para aplicativo Web, WebJobs, APIs REST e backends móveis
* alta disponibilidade e balanceamento de carga

## Rede Virtual

* conecta recursos a outros, a usuários na internet e a computadores locais
* extensão da rede local através de VPN ou do ExpressRoute (conexão privada direta, sem passar pela internet)
* balanceador de carga
* filtro de tráfego por grupo de segurança ou firewall
* conectar redes virtuais pela backbone da microsoft (sem passar pela internet)
* **NSG:** Network Security Group
  * prioridades **menores** são executadas antes (só importa mesmo se houver sobreposição de portas)
* **UDR:** User Defined Routes, controle das tabelas de roteamento

## Gateway VPN

* chave pré compartilhada
* baseado em política **~>** IP
* baseado em rota **~>** interface virtual (mais resilientes a alterações de topologia)
* duas instâncias por padrão **~>** alta disponibilidade 
  * uma ativa e a outra em espera
  * ativo/ativo **~>** um IP público para cada
* redundância de zona

## ExpressRoute

* não passa pela internet
* conexão com a rede local se chama Circuito do ExpressRoute
* cada local conectado com a nuvem tem um Curcuito
* a conexão pode ser
  * any to any **~>** VPN de IP
  * Ethernet ponto a ponto
  * conexão cruzada virtual por meio de um provedor
* permite conectividade direta com alguns serviços
* **conectividade global:** se ativada, permite a conexão de 2 redes locais através do ExpressRoute (sem passar pela internet)

## DNS

* rede anycast **~>** o servidor de DNS mais próximo responde a consulta (mais rápido)
* compatível com RBAC
* disponibiliza logs para monitoramento
* compatível com domínios privados
* não é possível comprar domínios no Azure DNS **~>** Serviço de Aplicativo ou terceiros

# 6 - Armazenamento

* cada conta de armazenamento tem um namespace exclusivo

## Redundância

* **Região Primária**

  * replicada 3 vezes
  * pode ser:
    * redundância local (LRS): 1 datacenter, 11 9s de disponibilidade no ano
    * redundância de zona (ZRS):3 zonas de disponibilidade, 12 9s de disponibilidade

* **Região Secundária** (opcional)

  * baseada nos pares de Regiões
  * ao criar a conta de armazenamento e escolher a região primária, é definida a região secundária correspondente
  * pode ser:
    * redundância geográfica (GRS) **~>** LRS nas duas regiões, 16 9s
    * redundância de zona geográfica (GZRS) **~>** ZRS na primária e LRS na secundária, 16 9s
  * por padrão, a região secundária não permite acesso, a menos que
    * seja iniciado failover ou
    * seja ativado o acesso de leitura através do RA-GRS ou RA-GZRS 

  * NÃO EXISTE SLA SOBRE O TEMPO PARA REPLICAR
  * **RPO:** Objetivo de Ponto de Recuperação
    * intervalo de tempo para sincrinização entre as redundâncias
    * normalmente abaixo de 15 min

## Blobs

* Armazenamento por objetos (um arquivo é um blob)
* Não estruturado **~>** sem restrição de tipos de dados
* acessível por navegadores web (URL), API REST, PowerShell ou CLI do Azure
* **cenários:** arquivos distribuídos, streaming, armazenamento de backups e de dados para análise
* **camadas:**
  * quente: acesso frequente **~>** imagens
  * esporádico: menos frequentes e armazenados por pelo menos 30 dias **~>** faturas
  * frio: pouco frequente e armazenados por pelo menso 90 dias
  * acesso aos arquivos: acessados raramente, armazenados por pelo menos 180 dias e com latência flexível **~>** backups de longo prazo
  * as camadas frio e acesso aos arquivos não estão disponíveis a nível de conta, mas as 4 estão disponíveis a nível de blob


## Arquivos do Azure

* compatilhamento via SMB ou NFS
* fileserver como SaaS
* gerenciável via web, PowerShell ou cmdlets **~>** scripts para automação

## Filas do Azure

* armazenamento de mensagens
* até 64 KB por mensagem
* usadas para criar lista de pendências de trabalho assíncrono
* pode ser gatilho para disparar uma Functions

## Discos do Azure

* volumes em nível de bloco
* gerenciados pela Azure
* usados em VMs

## Tabelas do Azure

* dados estruturados NoSQL (não relacionais)

## Migração para Azure

* plataforma de migração unificada
* iniciar, executar e acompanhar a migração
* migrar de infra local para Azure
* permite acesso a ferramentas de terceiros (ISVs, fornecedores independentes de software)
* Descoberta e avaliação, Migração de Servidor, Assistente de Migração de Dados (SQL Server), Migração de Banco de Dados, Assistente de Migração do Serviço de Aplicativo e Data Box (grandes quantidade de dados offline)
* Data Box: enviado dispositivo com capacidade de 80 TB
  * pode ser usado para transferir dados locais para a nuvem
  * pode ser usado para recuperação de desastre, copiando os dados da nuvem para o data box e enviando ele ao cliente para restauração
* AzCopy: ferramenta cli para transferência de arquivos, sincronização e até envio para outras nuvens
  * sincronização do tipo origem ~> destino, não bidirecional
* Gerenciador de Armazenamento: software de desktop, gerenciador de arquivos que usa AzCopy no backend
* Sincronização de Arquivos: instalado no fileserver local, faz a sincronização bidirecional

# 7 - Identidade, Acesso e Segurança

## Entra ID

* é o AD na nuvem
* pode se conectar ao AD local para adição de recursos
  * através do Entra Connect
  * usado para investigar tentativas de login suspeitas
* autenticação, Single Sing On
* permite o acesso somente por dispositivos conhecidos, independente da conta de usuário

## Entra Domain Services

* controlador de domínio sem precisar implantar, gerenciar ou aplicar patches
* replicação, criptografia e backups automáticos

* Autenticação: confirmar a identidade da pessoa, serviço ou dispositivo

* SSO: uma única identidade para acessar diversos serviços de provedores diferentes
* MFA: algo que o usuário saiba (pergunta), algo que o usuário tenha (código no email ou celular) ou algo que o usuário seja (biometria ou reconhecimento facial)
* Autenticação sem senha: pode ser configurada depois que dispositivo é reconhecido
  * Windows Hello, Microsoft Authenticador ou chaves FIDO2
* Identidades Externas: clientes ou fornecedores, podem trazer sua identidade de outro gerenciador como Google ou Facebook
* Acesso condicional: se o usuário está logando de um novo dispositivo, ou de uma nova localização, pode ser pedido outro fator de autenticação ou pode ser bloqueado automaticamente

## RBAC

* Controle de Acesso baseado em Função
* aplicado a:
  * uma assinatura ou coleção de assinaturas (grupo de gerenciamento)
  * um recurso ou grupo de recursos
* hierárquico: os escopos filhos herdam as permissões dos pais

## Zero Trust

* verifica cada solicitação como se tivesse sido originada em uma rede não controlada
* princípios:
  * Verificar de modo explícito
  * Privilégio mínimo, JIT (Just in Time) e JEA (Just Enough Access)
  * Pressupor violação

## Defesa em Profundidade

* Camadas
* Física **~>** Identidade e acesso **~>** perímetro (DDoS) **~>** rede (comunicação) **~>** computação (vms e dispositivos) **~>** aplicativo **~>** dados 

## Microsoft Defender

* nativo do Azure
* pode ser implantado localmente e em outras nuvens
* princípios:
  * Avaliar contínuamente
  * Proteger
  * Defender

# 8 - Custos

* Redução do CapEx (depesa de capital) e automento do OpEx (despesa de operação)
* Reserva de uso pode gerar desconto de até 72%
* algumas transferências de dados de entrada no Azure são gratuitos
* saída do Azure é sempre cobrada baseando-se na Zona

* **Calculadora de Preços:** estimativa de custos para provisionar recursos
  * tem cenários de exemplo para usar como ponto de partida
* **Calculadora TCO:** comparar custos de infra local com Azure
  * em 3 etapas:
    * Definir cargas de trabalho
    * Ajustar suposições
    * Exibir relatório

## Gerenciamento de Custos

* Custos dos recursos provisionados
* Alertas de custos, de crédito (para Contratos Enterprise) e de cota por departamento
* Tendência de gastos
* Pode ser configurada modificação ou suspensão de um recurso ao atingir um limite de orçamento
* É possível adicionar marcas (tags) em recursos para organização e automações
  * Marcas são conjuntos nome-valor
  * Marcas não são herdadas

# 9 - Governança e Conformidade

## Purview

* Exibição unificada de informações
* Descoberta automatizada multinuvem
* **Soluções de Risco e Conformidade**
  * Proteção de dados confidenciais entre nuvens
  * Conformidade Regulatória
* **Governança de Dados Unificada**
  * Gerenciamento de dados em Bancos diversos (inclusive AWS S3)
  * Mapa de patrimônio
  * Localização de dados confidenciais

## Policy

* Criar e gerenciar políticas que controlam ou auditam recursos
* **Iniciativas:** grupos de políticas relacionadas
* Realça os recursos que não estão em conformidade com as políticas criadas pelo usuário
* Pode ser configurado para impedir a criação de um recurso em não confirmidade
* As políticas são herdadas
* O Azure pode ajustar automaticamente recursos para entrarem em conformidade. Exemplo: adicionar uma marca à todos os recursos de um grupo

## Bloqueio de Recursos

* Proteção contra exclusões ou alterações mesmo com permissões
* São herdados
* Podem ser aplicados a um recurso, a um grupo de recursos ou a toda a assinatura
* Tipos:
  * Bloqueio somente de exclusão
  * Bloqueio de exclusão e alteração **~>** readonly
* Ao tentar alterar um recurso aparace uma mensagem informando o bloqueio
* Para alterar um recurso, o bloqueio deve ser retirado

## Portal de Confiança do Serviço

* Biblioteca de recursos e ferramentas sobre segurança, privacidade e conformidade

# 10 - Gerenciamento de Recursos

## Portal Azure

* Disponível em todos os datacenters **~>** resiliente à falhas
* Não requer tempo de inatividade para manutenção

## Cloud Shell

* Shell pelo navegador
* Pode ser usado em PowerShell ou CLI do Azure (Bash)
  * Ambas porem ser instaladas localmente em Windows, Linux e Mac
* Autenticado pelas credenciais do navegador

## Azure Arc

* Gerenciamento de várias nuvens
  * Servidores
  * Clusters Kubernetes
  * SQL Server

## Azure Resource Manager (ARM)

* Toda interação com recursos passa pelo ARM
* Infra as Code com modelos declarativos em JSON
* Aplicar marcas, atribuir a grupos, controle de acesso
* Modelos ARM ou Bicep
  * **Bicep:** linguagem declarativa mais simples

# 11 - Monitoramento

## Assistente do Azure

* Avalia os recursos em uso e faz recomendações
* Categorias: confiabilidade, segurança, desempenho, excelência operacional e custo

## Integridade do Serviço

* Informações da infraestrutura global do Azure
* Tanto recursos implantados na assinatura quanto gerais
* Armazena históricos
* Serviços:
  * **Status:** informações globais de interrupções de serviços
  * **Integridade do Serviço:** informações dos serviços e regiões da sua assinatura
  * **Resource Health:** informações de cada recurso utilizado na sua assinatura

## Azure Monitor

* Coletar, visualizar e analisar dados sobre seus recursos
* Compatível com recursos locais e várias nuvens
* Os dados podem disparar alertas, emails ou uma ação corretiva
* **Application Insights:** monitoramento de aplicativo
  * Instalado por SDK ou agente
  * Monitora tempo de resposta e taxa de falha

* ## Prova

* Quais componentes são criados em uma assinatura? Recursos e grupo de recursos
* Relatório de cobrança e faturas separados? Subscriptions
* Conectar recurso a uma rede virtual? Pontos de extremidade
* Acessar recursos a partir de clientes aprovados? Acesso condicional
* Avalia os recursos e faz recomendações? Assistente do Azure
* Informações sobre interrupção de serviço? Avisos de integridade
