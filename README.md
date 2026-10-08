🛡️ Governança e Segurança no Azure: Tags e Resource Locks

📋 Descrição do Projeto

Este projeto prático demonstra a implementação de políticas de governança e segurança no Microsoft Azure. O laboratório simula um ambiente corporativo com múltiplos locatários lógicos (Multitenant), onde equipes diferentes compartilham a mesma infraestrutura. O objetivo foi aplicar Tags para rastreamento de custos (FinOps) e Resource Locks para prevenção contra perda de dados (Data Loss Prevention) e erros humanos.

🏗️ Arquitetura e Recursos Utilizados

Azure Resource Group: Contêiner lógico central para organização.

Azure Storage Accounts (x2): Simulação de recursos consumidos por diferentes departamentos.

Azure Tags: Metadados para categorização de faturamento e ambiente.

Azure Resource Locks: Travas de segurança de infraestrutura.

🎯 Objetivos Alcançados

1. Estratégia de Tagging e FinOps

Criação de recursos e aplicação de Tags granulares (departamento e environment).

Configuração de infraestrutura pronta para alocação de custos interna (Chargeback/Showback), dividindo o consumo entre as equipes de Desenvolvimento e Operações.

Utilização de Tags para Descoberta de Recursos (Resource Discovery) e aplicação de filtros em larga escala.

2. Prevenção contra Perda de Dados (Resource Locks)

Delete Lock (CanNotDelete): Aplicado no nível do recurso (Storage Account) para proteger dados críticos contra exclusão acidental.

Read-Only Lock (Somente Leitura): Aplicado no nível do Grupo de Recursos para simular uma estratégia de congelamento de ambiente (Environment Freeze).

Herança de Bloqueios: Demonstração prática de que bloqueios no escopo pai (Resource Group) são herdados automaticamente pelos recursos filhos.

Sobreposição de Privilégios: Validação de que os Resource Locks superam permissões de RBAC, bloqueando modificações até mesmo para usuários com privilégio de Owner (Dono) da assinatura.

3. Gestão de Mudanças e Ciclo de Vida

Execução de testes de intrusão/modificação para validar a eficácia das travas no portal.

Simulação de uma "Janela de Manutenção", removendo as travas temporariamente para realizar alterações autorizadas e validando a restauração das permissões normais.

💡 Notas de Estudo (Foco na Certificação AZ-900)

Durante a execução deste projeto, os seguintes conceitos fundamentais foram validados:

Herança de Tags: Diferente dos Locks, Tags aplicadas a um Resource Group não são herdadas automaticamente pelos recursos filhos (requer Azure Policy).

Escopo de Bloqueio: A trava mais restritiva sempre vence. Um bloqueio de leitura no grupo impede a exclusão de um recurso, mesmo que o recurso tenha apenas uma trava de exclusão.

Nomes Exclusivos: Contas de Armazenamento no Azure exigem nomes globalmente exclusivos para formação do endpoint público.
