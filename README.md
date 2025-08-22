## Requisitos Funcionais

### Gestão de Usuários e Hierarquia (FOCO PRINCIPAL)
- Cadastro de usuários com 8 tipos hierárquicos
- Autenticação multifator para níveis administrativos
- Sistema de convites baseado em hierarquia
- Controle de sessões ativas por tipo de usuário
- Transição entre níveis com aprovação

### Hierarquia de Usuários (8 Níveis)
1. Super Administrador - Controle total do sistema
2. Administrador da Empresa/Estúdio - Gestão organizacional
3. Produtor Musical/Gerente de Projeto - Gestão de projetos
4. Compositor/Artista Principal - Proprietário de obras
5. Co-Autor/Colaborador - Participante em obras
6. Artista/Músico Convidado - Acesso limitado a projetos
7. Visualizador/Cliente - Apenas visualização autorizada
8. Usuário Suspenso - Acesso bloqueado temporariamente

### Gestão de Arquivos (SIMPLIFICADA)
- Upload seguro de arquivos musicais
- Organização por pastas/projetos
- Versionamento básico
- Sistema de tags simples
- Preview seguro sem download completo

### Controle de Acesso (CORE DO SISTEMA)
- Matriz de permissões rigorosa por hierarquia
- Proprietário tem controle total sobre seus arquivos
- Compartilhamento apenas com aprovação explícita
- Revogação imediata de acessos
- Links temporários com expiração

### Auditoria e Rastreamento (ANTI-FURTO)
- Log detalhado de TODOS os acessos
- Registro de IP, dispositivo, horário
- Histórico completo de downloads
- Alertas automáticos para atividades suspeitas
- Relatórios de atividade por usuário/arquivo

### Proteção Contra Furto (ESSENCIAL)
- Marca d'água digital em todos os downloads
- Identificação única do usuário em cada arquivo baixado
- Detecção de tentativas de acesso não autorizado
- Bloqueio automático de contas suspeitas
- Sistema de denúncia de uso indevido

## Requisitos Não Funcionais

### Segurança (FOCO ANTI-FURTO)
- Criptografia AES-256 para arquivos
- Comunicação HTTPS obrigatória
- Autenticação forte para todos os usuários
- Logs imutáveis e assinados digitalmente
- Backup seguro e criptografado

### Performance
- Upload de arquivos até 200MB
- Tempo de resposta < 3 segundos
- Suporte a 500 usuários simultâneos
- Disponibilidade 99.5%
- Backup diário automatizado

### Usabilidade
- Interface intuitiva por tipo de usuário
- Dashboard personalizado por hierarquia
- Notificações em tempo real
- Suporte a dispositivos móveis
- Onboarding simples

## Regras de Negócio

### Hierarquia e Controle de Acesso

#### **Matriz de Permissões Simplificada**

| Ação | Super Admin | Admin Empresa | Produtor | Compositor | Co-Autor | Convidado | Visualizador | Suspenso |
|------|-------------|---------------|----------|------------|----------|-----------|--------------|----------|
| Gerenciar usuários | ✅ | ✅ (sua org) | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Criar projetos | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ |
| Upload arquivos | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ (limitado) | ❌ | ❌ |
| Download arquivos | ✅ | ✅ | ✅ | ✅ (próprios) | ✅ (autorizados) | ✅ (autorizados) | ❌ | ❌ |
| Compartilhar | ✅ | ✅ | ✅ | ✅ (próprios) | ❌ | ❌ | ❌ | ❌ |
| Ver logs | ✅ | ✅ (sua org) | ✅ (projetos) | ✅ (próprios) | ❌ | ❌ | ❌ | ❌ |
| Excluir arquivos | ✅ | ❌ | ❌ | ✅ (próprios) | ❌ | ❌ | ❌ | ❌ |

### Proteção Anti-Furto (REGRAS PRINCIPAIS)

#### **Propriedade e Controle**
- Apenas o uploader original é proprietário inicial
- Proprietário define quem pode acessar seus arquivos
- Transferência de propriedade requer confirmação dupla
- Co-autoria deve ser definida no momento do upload
- Arquivos sem proprietário ativo ficam bloqueados

#### **Rastreamento Obrigatório**
- Todo acesso a arquivo é registrado (visualização, download, compartilhamento)
- Downloads recebem marca d'água com ID do usuário e timestamp
- Tentativas de acesso negado são registradas
- IPs suspeitos são bloqueados automaticamente
- Atividade fora do horário normal gera alerta

#### **Compartilhamento Controlado**
- Compartilhamento requer aprovação do proprietário
- Links temporários expiram automaticamente (máximo 7 dias)
- Número limitado de downloads por link
- Revogação imediata de acessos compartilhados
- Notificação ao proprietário a cada acesso

#### **Detecção de Atividades Suspeitas**
- Download em massa (mais de 10 arquivos/hora)
- Acesso de múltiplos IPs na mesma conta
- Tentativas de acesso a arquivos não autorizados
- Login fora do horário habitual do usuário
- Múltiplas tentativas de senha incorreta

### Hierarquia e Transições

#### **Promoção de Usuários**
- **Convidado → Co-Autor:** Aprovação do Compositor + histórico limpo
- **Co-Autor → Compositor:** Upload de obra original própria
- **Compositor → Produtor:** Aprovação do Admin + 6 meses de atividade
- **Produtor → Admin:** Aprovação do Super Admin + recomendação

#### **Rebaixamento Automático**
- Inatividade por 60 dias: rebaixamento automático
- Atividade suspeita: suspensão imediata
- Violação de políticas: rebaixamento ou suspensão
- Denúncia comprovada: investigação e possível suspensão

### Auditoria e Compliance

#### **Logs Obrigatórios**
- Data/hora de todos os acessos
- IP e dispositivo utilizado
- Ação realizada (visualizar, baixar, compartilhar)
- Duração da sessão
- Arquivos acessados

#### **Retenção de Dados**
- Logs de acesso: 5 anos
- Arquivos de usuários ativos: indefinido
- Arquivos de usuários inativos: 2 anos
- Backup de segurança: 1 ano
- Relatórios de auditoria: 3 anos

#### **Alertas Automáticos**
- Acesso suspeito: notificação imediata ao proprietário
- Download não autorizado: alerta ao admin da organização
- Tentativa de furto: bloqueio automático + notificação
- Atividade anômala: relatório semanal aos administradores

### Políticas de Uso

#### **Responsabilidades por Hierarquia**
- **Compositores:** Responsáveis pela originalidade de suas obras
- **Produtores:** Responsáveis pela supervisão de projetos
- **Admins:** Responsáveis pela segurança organizacional
- **Super Admin:** Responsável pela integridade do sistema

#### **Violações e Penalidades**
- 1ª violação: advertência + treinamento obrigatório
- 2ª violação: suspensão temporária (7 dias)
- 3ª violação: rebaixamento de hierarquia
- Furto comprovado: banimento permanente + processo legal
