# Gerenciando-Politicas-em-Acessos-Azure
Resposta ao desafio DIO - Gerenciando Politicas em Acessos Azure
O **Azure Trusted Service Portal** (Portal de Confiança do Serviço do Azure) é uma plataforma da Microsoft que centraliza informações sobre a conformidade e a segurança dos serviços do Azure. Ele oferece uma visão detalhada das práticas de segurança adotadas pela Microsoft para garantir que os serviços na nuvem do Azure estejam alinhados com normas regulatórias e melhores práticas globais.

Aqui estão alguns dos principais pontos sobre o portal:

1. **Conformidade**: O portal exibe informações sobre certificações e auditorias de conformidade que os serviços do Azure obtiveram, como **ISO/IEC 27001**, **SOC 1/2/3**, **GDPR**, entre outras. Isso permite que os clientes verifiquem se os serviços que estão utilizando atendem a regulamentações específicas.

2. **Transparência**: A Microsoft fornece detalhes sobre como ela implementa controles de segurança e privacidade para proteger os dados dos clientes. Isso inclui como os dados são processados, armazenados e gerenciados, dando maior confiança às empresas que estão migrando ou já utilizam a nuvem.

3. **Documentação**: O portal oferece acesso a documentos que descrevem a arquitetura de segurança, políticas e procedimentos de cada serviço do Azure. Isso é útil para auditores, equipes de compliance e profissionais de segurança, pois podem analisar em detalhes como a segurança está sendo tratada.

4. **Acesso a relatórios**: Empresas podem obter relatórios de auditorias e certificações diretamente no portal. Esses relatórios são fundamentais para mostrar a clientes, parceiros e autoridades regulatórias que os serviços utilizados estão em conformidade com requisitos específicos.

5. **Ferramentas de avaliação de risco**: O portal também oferece ferramentas e recursos para ajudar as empresas a avaliar e gerenciar riscos ao usar serviços do Azure. Isso facilita a tomada de decisões em relação à adoção de serviços baseados em suas necessidades de segurança e conformidade.

O Azure Trusted Service Portal, portanto, é uma fonte importante para qualquer empresa que precisa garantir que seus dados e operações estejam seguros e em conformidade dentro da nuvem Azure.
### Bloqueios de **Delete** e **Read-Only** 
Os bloqueios de **Delete** e **Read-Only** no Azure são mecanismos de proteção para evitar alterações acidentais ou deletações em recursos críticos. Esses bloqueios são aplicados no nível de recursos ou grupos de recursos e garantem que ações específicas não possam ser executadas, ajudando a proteger a integridade dos sistemas e dos dados. Vamos ver como cada um funciona:

### 1. **Bloqueio de Delete (Exclusão)**
O bloqueio de exclusão impede que um recurso ou grupo de recursos seja deletado acidentalmente. Isso é especialmente útil para proteger recursos que são críticos para o funcionamento de uma aplicação ou infraestrutura. Quando um bloqueio de **Delete** é aplicado, o recurso ainda pode ser modificado, mas qualquer tentativa de deletá-lo será bloqueada.

- **Como funciona**: O bloqueio é aplicado ao nível de recursos individuais, grupos de recursos ou assinaturas inteiras. Quando alguém tenta excluir um recurso protegido com esse bloqueio, o Azure impede a ação e gera uma mensagem de erro, informando que o bloqueio está em vigor.
  
- **Casos de uso**: Aplicar a proteção de exclusão para recursos essenciais como bancos de dados, VMs ou serviços de armazenamento críticos, garantindo que mesmo com permissões administrativas a exclusão acidental não ocorra.

### 2. **Bloqueio de Read-Only (Somente leitura)**
O bloqueio de **Read-Only** impede que qualquer modificação seja feita em um recurso ou grupo de recursos. Ele garante que os dados e as configurações atuais do recurso não sejam alterados, mas permite que o recurso ainda seja lido ou consultado.

- **Como funciona**: Quando aplicado, o bloqueio de somente leitura permite operações que não modifiquem o estado do recurso (operações GET, por exemplo). No entanto, impede operações que possam alterar o recurso, como atualizações ou modificações nas configurações. Tentativas de realizar essas operações bloqueadas resultarão em erro.
  
- **Casos de uso**: Ideal para ambientes onde os dados ou configurações não devem ser alterados, como em sistemas de produção que precisam de estabilidade. Também pode ser útil durante auditorias, onde é importante garantir que os dados sejam visualizados, mas não alterados.

### Onde configurar os bloqueios?
- **Portal do Azure**: Os bloqueios podem ser configurados diretamente no portal. No painel de um recurso ou grupo de recursos, há a opção de aplicar bloqueios na aba "Locks" (Bloqueios). Lá, é possível definir se o bloqueio será de exclusão ou de somente leitura.
  
- **CLI e PowerShell**: Também é possível configurar bloqueios usando a CLI do Azure ou o PowerShell, o que é útil para automação ou implementação de políticas de governança.

### Considerações
- Mesmo que um administrador ou uma pessoa com permissões elevadas tente realizar uma operação restrita por esses bloqueios, ela será bloqueada, garantindo uma camada adicional de proteção.
- Os bloqueios são uma medida essencial de governança em ambientes de nuvem, especialmente em grandes organizações ou projetos críticos onde a segurança e a integridade dos recursos são fundamentais.

Esses bloqueios são bastante úteis para evitar alterações inadvertidas e garantir a segurança e a estabilidade da infraestrutura no Azure.

### Microsoft Purview
O **Microsoft Purview** é uma plataforma unificada de governança e conformidade de dados oferecida pela Microsoft. Ele foi projetado para ajudar organizações a gerenciar e governar seus dados de forma abrangente, possibilitando o entendimento, a proteção e o gerenciamento dos dados onde quer que eles estejam, seja em ambientes on-premises (locais), na nuvem ou em serviços SaaS.

### Funcionalidades principais do Microsoft Purview

1. **Catalogação de Dados (Data Catalog)**:
   - O Microsoft Purview cria um catálogo centralizado dos dados da organização, oferecendo uma visão abrangente de todos os ativos de dados, independentemente de onde eles estejam armazenados. Isso facilita a busca e descoberta de dados pelos usuários.
   - Ele permite a **classificação automática** dos dados, atribuindo rótulos (tags) com base em tipos sensíveis de informações, como números de cartão de crédito, informações pessoais, ou dados confidenciais.
   - A busca inteligente no catálogo permite que usuários identifiquem e acessem rapidamente os dados relevantes.

2. **Mapa de Dados (Data Map)**:
   - O Purview cria um **mapa de dados** que fornece uma visão completa do fluxo de dados dentro da organização. Isso inclui como os dados se movem entre sistemas e como eles são transformados ao longo do tempo.
   - Esse mapa é construído automaticamente a partir de varreduras e integrações com diversas fontes de dados, como bancos de dados, data lakes e outros serviços na nuvem ou locais.

3. **Governança de Dados**:
   - O Microsoft Purview ajuda a garantir que os dados da organização estejam em conformidade com políticas regulatórias e internas, como **GDPR**, **HIPAA**, entre outras. Isso é feito através da definição de políticas de acesso e uso de dados com base em regras de conformidade e privacidade.
   - Com o **role-based access control (RBAC)**, o Purview permite controlar quem tem acesso a diferentes conjuntos de dados e sob quais condições, garantindo a segurança das informações.

4. **Gerenciamento de Metadados**:
   - O Microsoft Purview permite o **gerenciamento de metadados** (dados sobre os dados), o que facilita o rastreamento da linhagem dos dados e ajuda a documentar como os dados são transformados em diferentes partes do pipeline.
   - Ele automatiza o processo de captura de metadados e oferece uma visão consolidada, permitindo que as equipes compreendam melhor as fontes e a transformação dos dados.

5. **Proteção de Dados Sensíveis**:
   - Com a integração ao **Microsoft Information Protection**, o Purview oferece ferramentas para proteger dados sensíveis, aplicando rótulos de sensibilidade e políticas de segurança. Por exemplo, ele pode impedir que dados pessoais identificáveis (PII) sejam compartilhados sem as permissões adequadas.
   - Também é possível criar alertas e regras automáticas para garantir que dados críticos estejam sempre protegidos, independentemente de onde estejam armazenados ou compartilhados.

6. **Linhas de Dados (Data Lineage)**:
   - O Purview oferece rastreamento de **linhagem de dados**, que mostra o ciclo de vida completo de um dado desde a sua origem até o seu uso final, passando por todos os processos de transformação. Isso é fundamental para entender o impacto de alterações nos dados e garantir a integridade nas análises.
   - Isso ajuda não apenas na governança, mas também na resolução de problemas e na auditoria, uma vez que fica claro como e onde os dados foram modificados.

7. **Integrações**:
   - O Microsoft Purview se integra com várias ferramentas e serviços, tanto no ecossistema da Microsoft quanto fora dele, como o **Azure Data Lake**, **SQL Server**, **Power BI**, **Azure Synapse Analytics**, e até serviços de terceiros como o **Amazon S3** e outras fontes externas.
   - Essa interoperabilidade facilita a governança em múltiplas plataformas e ambientes, garantindo uma gestão holística dos dados da organização.

8. **Insights e Relatórios**:
   - O Purview oferece painéis e relatórios que fornecem insights sobre a conformidade de dados, o uso de dados sensíveis e outras métricas importantes para a governança. Isso é útil para auditar o uso de dados e garantir que a organização esteja seguindo as melhores práticas e exigências regulatórias.
   - Ele também permite o rastreamento de atividades de dados, como quem acessou, modificou ou compartilhou determinados conjuntos de dados.

### Benefícios do Microsoft Purview

- **Visão unificada dos dados**: Permite que as organizações tenham uma visão única e centralizada de seus dados, facilitando a governança e a conformidade em diferentes ambientes.
  
- **Automação da descoberta de dados**: A automação na catalogação e classificação de dados reduz o trabalho manual e aumenta a precisão na identificação de dados sensíveis ou importantes.

- **Segurança e conformidade aprimoradas**: Com políticas e controles robustos, o Purview ajuda a garantir que os dados estejam protegidos e em conformidade com regulamentações internacionais e exigências internas.

- **Acesso mais eficiente aos dados**: O Purview facilita a descoberta e o acesso aos dados relevantes para as diferentes equipes dentro da organização, melhorando a eficiência das operações e das análises.

### Caso de uso
Imagine uma grande organização que precisa gerenciar dados em ambientes híbridos, combinando armazenamento local, serviços na nuvem e ferramentas de análise como o Power BI. O Microsoft Purview fornece uma visão consolidada de onde os dados estão, como eles fluem, quem os acessa e se estão em conformidade com regulamentações como a GDPR. Isso garante que tanto a equipe de TI quanto as áreas de negócio possam usar os dados com segurança, agilidade e controle.

### Azure Policy

O **Azure Policy** é uma solução do Azure que permite criar, aplicar e gerenciar regras e políticas para garantir que os recursos da sua organização na nuvem estejam em conformidade com padrões de governança, segurança e compliance. Com o Azure Policy, é possível definir o que pode ou não ser feito dentro do ambiente do Azure, ajudando a manter controle sobre a utilização de recursos e garantindo que as melhores práticas sejam seguidas.

### Funcionamento do Azure Policy

1. **Definição de Políticas**:
   - Uma **política** no Azure Policy é um conjunto de regras que define o comportamento desejado para recursos do Azure. Ela pode impor restrições, permitir ou negar determinadas ações ou exigir configurações específicas em recursos.
   - As políticas são escritas em um formato JSON, onde são definidas condições (como verificar o tipo de recurso ou tags) e efeitos (como permitir, negar ou auditar uma ação).

2. **Políticas Integradas (Built-in Policies)**:
   - O Azure Policy oferece várias políticas integradas para diferentes casos de uso, como gerenciamento de recursos, compliance com regulamentações (por exemplo, GDPR), ou exigência de certas configurações de segurança (como criptografia ou firewalls). Você pode usar essas políticas prontas ou customizá-las de acordo com as necessidades da sua organização.
   
3. **Definição de Iniciativas (Initiatives)**:
   - Uma **iniciativa** é um agrupamento de políticas. Em vez de aplicar políticas individualmente, você pode criar uma iniciativa que contenha várias políticas relacionadas. Isso facilita a aplicação de um conjunto de regras de governança de forma consistente.
   - Por exemplo, uma iniciativa de conformidade com a **ISO 27001** pode agrupar várias políticas de segurança para garantir que todos os recursos estejam em conformidade com essa norma.

4. **Efeitos das Políticas**:
   As políticas podem ter diferentes tipos de efeitos, dependendo de como você deseja controlar os recursos:

   - **Deny (Negar)**: Impede a criação ou modificação de recursos que não estejam em conformidade com a política. Por exemplo, pode impedir a criação de VMs em uma determinada região ou impedir a criação de recursos sem criptografia.
   - **Audit (Auditar)**: Registra uma auditoria quando um recurso não está em conformidade com a política, mas não impede a ação. Isso é útil para identificar recursos que não atendem aos padrões sem bloquear operações.
   - **Append (Anexar)**: Adiciona propriedades a um recurso se ele não estiver em conformidade. Por exemplo, pode anexar uma tag obrigatória a um recurso se ele for criado sem ela.
   - **DeployIfNotExists (Implantar se não existir)**: Implementa automaticamente um recurso ou configuração se ele não existir ou se não estiver conforme. Por exemplo, pode garantir que todas as VMs tenham uma solução de monitoramento configurada.
   - **Modify (Modificar)**: Altera ou corrige automaticamente as propriedades do recurso que estão fora de conformidade, como alterar a configuração de um serviço de backup ou habilitar logs de diagnóstico.

5. **Escopos de Aplicação**:
   - As políticas podem ser aplicadas em diferentes níveis de escopo no Azure, como **assinatura**, **grupo de recursos** ou em **recursos individuais**. Isso oferece flexibilidade para controlar recursos em diferentes partes da infraestrutura da organização.
   - Ao aplicar uma política ou iniciativa, todos os recursos dentro daquele escopo são avaliados de acordo com as regras definidas.

6. **Avaliação de Conformidade**:
   - Uma vez que uma política ou iniciativa é aplicada, o Azure Policy automaticamente avalia a conformidade dos recursos com as regras definidas. Você pode monitorar o estado de conformidade através de um painel no portal do Azure, que mostra quais recursos estão ou não em conformidade com cada política.
   - Também é possível ver detalhes sobre por que um recurso específico não está em conformidade e tomar ações corretivas.

### Casos de Uso do Azure Policy

1. **Governança de Custos**:
   - Políticas podem ser aplicadas para impedir que certos tipos de recursos caros sejam criados, como VMs de alta performance, ou que recursos sejam criados em regiões específicas que têm maior custo.
   
2. **Segurança e Compliance**:
   - Para atender a normas de conformidade como **GDPR**, **HIPAA** ou **ISO 27001**, as políticas podem garantir que os dados estejam devidamente criptografados, que os backups sejam configurados e que logs de auditoria sejam habilitados para recursos críticos.
   
3. **Gerenciamento de Tags**:
   - Você pode usar o Azure Policy para garantir que todos os recursos tenham as tags adequadas para identificação e gerenciamento, como tags de projetos, departamentos ou proprietários. Isso ajuda a garantir um controle preciso dos recursos no Azure.
   
4. **Restrição de Localização**:
   - Em algumas organizações, há requisitos de compliance que obrigam os dados a serem armazenados em regiões geográficas específicas. O Azure Policy pode restringir a criação de recursos em regiões fora das permitidas.

5. **Imposição de Padrões**:
   - Para garantir a consistência em configurações de segurança, como VMs que devem ter firewalls habilitados ou discos criptografados, o Azure Policy pode ser utilizado para impedir a criação de recursos que não atendam a esses padrões.

### Exemplo de Política Simples

Um exemplo básico de política que impede a criação de VMs em uma região específica seria algo assim em JSON:

```json
{
  "if": {
    "field": "location",
    "equals": "eastus"
  },
  "then": {
    "effect": "deny"
  }
}
```

Neste exemplo, a condição `if` verifica se o campo `location` é igual a "eastus" e, se for, a política impede a criação do recurso com o efeito `deny`.

### Integração com Azure Blueprints

O **Azure Policy** também pode ser integrado com **Azure Blueprints**, que permite implantar políticas junto com templates de infraestrutura e outros artefatos, como definições de RBAC. Isso facilita a criação de ambientes de forma consistente, com governança e segurança aplicadas automaticamente.

### Benefícios do Azure Policy

- **Automatização da Governança**: Ao automatizar o processo de imposição de regras, as políticas reduzem a necessidade de intervenções manuais, garantindo conformidade em escala.
  
- **Flexibilidade e Controle**: Com a capacidade de aplicar políticas em diversos níveis (de assinatura a recursos específicos) e ajustar efeitos, você tem controle detalhado sobre como gerenciar seu ambiente Azure.

- **Conformidade Contínua**: O Azure Policy monitora continuamente os recursos para garantir que estejam em conformidade com as políticas, emitindo alertas e impedindo ações que possam violar as regras de governança.

Em resumo, o **Azure Policy** é uma ferramenta poderosa para garantir governança e segurança no ambiente Azure, permitindo que as organizações implementem políticas de conformidade consistentes e garantam o controle adequado sobre a infraestrutura na nuvem.
