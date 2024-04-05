# AZR - 2/11
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

## Alta Disponibilidade

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

# 4 - Arquitetura

# 5 - Computação e Rede

# 6 - Armazenamento

# 7 - Identidade, Acesso e Segurança

# 8 - Custos

# 9 - Governança e Conformidade

# 10 - Gerenciamento de Recursos

# 11 - Monitoramento