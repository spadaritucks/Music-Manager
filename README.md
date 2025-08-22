# Music-Manager

## Requisitos Funcionais

### Gestão de Usuários
• Cadastro de compositores e artistas com diferentes níveis de acesso
• Autenticação multifator obrigatória
• Perfis de usuário com informações profissionais
• Sistema de convites para novos usuários
• Controle de sessões ativas

### Gestão de Arquivos
• Upload de arquivos musicais (áudio, partituras, letras, demos)
• Versionamento automático de arquivos
• Organização por projetos/álbuns
• Sistema de tags e metadados
• Preview seguro de arquivos sem download
• Conversão automática para formatos seguros

### Controle de Acesso
• Definição de proprietários de arquivos
• Sistema de permissões granulares (visualizar, editar, compartilhar)
• Compartilhamento temporário com expiração
• Aprovação de acesso por parte do proprietário
• Revogação imediata de permissões

### Auditoria e Rastreamento
• Log completo de todas as ações (acesso, download, modificação)
• Registro de IP, dispositivo e localização
• Histórico de compartilhamentos
• Relatórios de atividade por usuário/arquivo
• Alertas de atividades suspeitas

### Proteção Digital
• Marca d'água digital em arquivos
• Criptografia de arquivos em repouso e trânsito
• Assinatura digital para comprovar autoria
• Sistema de fingerprinting de áudio
• Backup automático criptografado

## Requisitos Não Funcionais

### Segurança
• Criptografia AES-256 para arquivos
• Comunicação via HTTPS/TLS 1.3
• Armazenamento em servidores seguros (AWS/Azure)
• Conformidade com LGPD
• Testes de penetração regulares

### Performance
• Upload de arquivos até 500MB
• Tempo de resposta < 2 segundos para operações básicas
• Suporte a 1000 usuários simultâneos
• Disponibilidade 99.9%
• Backup diário automatizado

### Usabilidade
• Interface intuitiva e responsiva
• Suporte a dispositivos móveis
• Múltiplos idiomas (português, inglês)
• Acessibilidade WCAG 2.1
• Onboarding guiado para novos usuários

### Escalabilidade
• Arquitetura em nuvem escalável
• Suporte a crescimento de 50% ao ano
• Balanceamento de carga automático
• Armazenamento elástico

## Regras de Negócio

### Propriedade Intelectual
• Apenas o criador original pode ser proprietário inicial
• Transferência de propriedade requer assinatura digital
• Co-autoria deve ser definida no momento do upload
• Arquivos órfãos (sem proprietário ativo) ficam em quarentena

### Acesso e Compartilhamento
• Proprietário tem controle total sobre o arquivo
• Compartilhamento requer aprovação explícita do proprietário
• Acesso temporário expira automaticamente
• Usuários inativos por 90 dias têm acesso suspenso
• Downloads são limitados e rastreados

### Auditoria e Compliance
• Todos os acessos são registrados por no mínimo 7 anos
• Alterações em arquivos geram nova versão automaticamente
• Exclusão de arquivos requer confirmação dupla
• Relatórios de auditoria são gerados mensalmente
• Violações de segurança são reportadas em 24h

### Proteção Contra Furto
• Arquivos baixados recebem marca d'água com ID do usuário
• Sistema detecta uploads de arquivos similares
• Alertas automáticos para atividades suspeitas
• Bloqueio imediato de contas com comportamento malicioso
• Processo formal para disputa de autoria

### Retenção e Backup
• Arquivos são mantidos por no mínimo 10 anos
• Backup incremental diário
• Backup completo semanal em localização geográfica diferente
• Recuperação de arquivos em até 4 horas
• Versionamento mantido por 2 anos

### Monetização
• Planos diferenciados por volume de armazenamento
• Funcionalidades premium para usuários pagantes
• Taxa por transferência de propriedade
• Desconto para estúdios com múltiplos usuários

Quer que eu detalhe alguma seção específica ou adicione outros aspectos ao sistema?

> Ok, ficou bom, mas como ficar a hieraquia de tipos de usuarios?

> Vou definir uma hierarquia de usuários estruturada para o sistema de proteção de arquivos musicais:

## Hierarquia de Tipos de Usuários

### 1. Super Administrador
Nível de Acesso: Máximo
• Gerenciamento completo do sistema
• Criação e remoção de administradores
• Configuração de políticas globais de segurança
• Acesso a todos os logs e relatórios de auditoria
• Backup e recuperação do sistema
• Definição de preços e planos
• Resolução final de disputas de autoria

### 2. Administrador da Empresa/Estúdio
Nível de Acesso: Alto
• Gerenciamento de usuários da sua organização
• Criação de grupos e projetos
• Definição de políticas internas
• Relatórios de atividade da empresa
• Aprovação de novos usuários
• Configuração de permissões organizacionais
• Não tem acesso aos arquivos dos usuários (apenas metadados)

### 3. Produtor Musical/Gerente de Projeto
Nível de Acesso: Médio-Alto
• Criação e gerenciamento de projetos
• Convite de artistas para projetos específicos
• Visualização de progresso dos trabalhos
• Aprovação de compartilhamentos dentro do projeto
• Relatórios de atividade do projeto
• Pode ter acesso a arquivos mediante autorização do proprietário

### 4. Compositor/Artista Principal
Nível de Acesso: Médio
• Proprietário de seus arquivos originais
• Upload e gerenciamento de suas obras
• Definição de co-autores
• Controle total sobre compartilhamento de seus arquivos
• Criação de colaborações
• Transferência de propriedade
• Visualização de logs de seus arquivos

### 5. Co-Autor/Colaborador
Nível de Acesso: Médio-Limitado
• Acesso a arquivos onde é co-autor
• Upload de versões/contribuições
• Não pode excluir arquivos originais
• Pode compartilhar apenas com aprovação do autor principal
• Visualização limitada de logs

### 6. Artista/Músico Convidado
Nível de Acesso: Baixo-Médio
• Acesso apenas a projetos específicos onde foi convidado
• Upload de contribuições (gravações, ideias)
• Não pode alterar arquivos principais
• Compartilhamento muito restrito
• Acesso temporário baseado no projeto

### 7. Visualizador/Cliente
Nível de Acesso: Baixo
• Apenas visualização de arquivos autorizados
• Não pode fazer download
• Não pode compartilhar
• Acesso apenas via link temporário
• Usado para apresentações a gravadoras, clientes, etc.

### 8. Usuário Suspenso
Nível de Acesso: Mínimo
• Acesso bloqueado temporariamente
• Pode visualizar apenas seus próprios arquivos
• Não pode fazer upload ou compartilhar
• Não pode acessar projetos colaborativos
• Mantém propriedade dos arquivos

## Matriz de Permissões por Tipo

| Ação | Super Admin | Admin Empresa | Produtor | Compositor | Co-Autor | Convidado | Visualizador |
|------|-------------|---------------|----------|------------|----------|-----------|--------------|
| Gerenciar usuários | ✅ | ✅ (sua org) | ❌ | ❌ | ❌ | ❌ | ❌ |
| Criar projetos | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ |
| Upload arquivos | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ (limitado) | ❌ |
| Excluir arquivos | ✅ | ❌ | ❌ | ✅ (próprios) | ❌ | ❌ | ❌ |
| Transferir propriedade | ✅ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ |
| Ver logs completos | ✅ | ✅ (sua org) | ✅ (projetos) | ✅ (próprios) | ❌ | ❌ | ❌ |
| Resolver disputas | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |

## Regras de Transição Entre Níveis

### Promoção
• **Convidado → Co-Autor:** Aprovação do Compositor Principal
• **Co-Autor → Compositor:** Criação de obra original própria
• **Compositor → Produtor:** Aprovação do Admin da Empresa + histórico
• **Produtor → Admin:** Aprovação do Super Admin

### Rebaixamento
• **Automático:** Por inatividade (90 dias)
• **Manual:** Por violação de políticas
• **Temporário:** Durante investigações de segurança

## Casos Especiais

### **Conta Corporativa**
• Representa a empresa/estúdio como entidade
• Pode ser proprietária de obras "work for hire"
• Gerenciada pelos Administradores da Empresa

### **Conta de Projeto**
• Criada para colaborações específicas
• Propriedade compartilhada entre participantes
• Dissolução automática após conclusão

### **Conta de Emergência**
• Acesso temporário para situações críticas
• Logs detalhados de todas as ações
• Expiração automática em 24h
