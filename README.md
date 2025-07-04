# 🚁 DroneCore - Sistema de Gestão para Empresas de Drone

Um sistema completo de gestão empresarial desenvolvido especificamente para empresas que prestam serviços com drones, incluindo mapeamento, inspeção e monitoramento agrícola.

## ✨ Funcionalidades

### 🎯 Gestão de Tarefas
- Criação e acompanhamento de missões
- Sistema de prioridades e status
- Anexo de arquivos KML e links do Google Maps
- Controle de hectares e valores de serviço
- Acompanhamento de progresso com fotos

### 👥 Gestão de Clientes
- Cadastro completo de clientes
- Histórico de serviços
- Controle de status (ativo/inativo)
- Sistema de dívidas e pagamentos

### 🚗 Gestão de Recursos
- Controle de frota de drones
- Gestão de veículos
- Status de disponibilidade
- Histórico de uso

### 👨‍💼 Gestão de Usuários
- Sistema de roles (Admin/Employee)
- Controle de acesso por funcionalidade
- Autenticação segura com JWT

### 💰 Gestão Financeira
- Controle de entradas e saídas
- Sistema de dívidas de clientes
- Registro de pagamentos
- Relatórios financeiros

### 📊 Dashboard e Relatórios
- Dashboard com métricas em tempo real
- Relatórios personalizados
- Exportação em PDF
- Gráficos e estatísticas

## 🛠️ Tecnologias Utilizadas

### Frontend
- **React 18** com TypeScript
- **Vite** para build e desenvolvimento
- **Tailwind CSS** para estilização
- **Shadcn/ui** para componentes
- **React Router** para navegação
- **React Query** para gerenciamento de estado
- **Axios** para requisições HTTP

### Backend
- **Node.js** com Express
- **Prisma ORM** para banco de dados
- **MySQL** como banco de dados
- **JWT** para autenticação
- **bcryptjs** para criptografia
- **CORS** para segurança

### Banco de Dados
- **MySQL** (compatível com MariaDB)
- **Prisma Migrations** para versionamento
- **Relacionamentos** com foreign keys

## 🚀 Deploy Rápido

### Opção 1: Script Automatizado
```bash
# Dar permissão de execução
chmod +x deploy.sh

# Executar script de deploy
./deploy.sh
```

### Opção 2: Manual
```bash
# 1. Instalar dependências
cd server && npm install
cd ../dronecore-dashboard-ui && npm install

# 2. Configurar banco de dados
cd ../server
# Criar arquivo .env com suas configurações
npm run prisma:generate
npm run prisma:migrate
npm run prisma:init

# 3. Build do frontend
cd ../dronecore-dashboard-ui
npm run build
```

## 📋 Pré-requisitos

- Node.js 18+ 
- npm ou yarn
- MySQL 8.0+ ou MariaDB 10.5+
- Git

## 🗄️ Configuração do Banco de Dados

### Local (Desenvolvimento)
```bash
# Instalar MySQL localmente ou usar Docker
docker run --name mysql-dronecore -e MYSQL_ROOT_PASSWORD=password -e MYSQL_DATABASE=dronecore -p 3306:3306 -d mysql:8.0
```

### Hostgator (Produção)
1. Acesse o painel da Hostgator
2. Vá para "Bancos de Dados" > "MySQL Databases"
3. Crie um banco chamado `dronecore`
4. Crie um usuário e associe ao banco
5. Use a string de conexão fornecida

### Variáveis de Ambiente
Crie um arquivo `.env` na pasta `server/`:
```env
DATABASE_URL="mysql://usuario:senha@localhost:3306/dronecore"
JWT_SECRET="sua-chave-secreta-super-segura-aqui"
PORT=3001
NODE_ENV=development
```

## 🌐 Deploy em Produção

### Backend (Railway - Gratuito)
1. Acesse [railway.app](https://railway.app)
2. Conecte seu repositório GitHub
3. Configure as variáveis de ambiente
4. Deploy automático

### Frontend (Vercel - Gratuito)
1. Acesse [vercel.com](https://vercel.com)
2. Conecte seu repositório GitHub
3. Configure o diretório: `dronecore-dashboard-ui`
4. Deploy automático

### Banco de Dados (Alternativas Gratuitas)
- **PlanetScale**: MySQL gratuito até 1GB
- **Supabase**: PostgreSQL gratuito até 500MB
- **Neon**: PostgreSQL gratuito

## 🔐 Credenciais Padrão

Após a inicialização do banco, você pode fazer login com:
- **Email**: `admin@dronecore.com`
- **Senha**: `admin123`

⚠️ **Importante**: Altere essas credenciais em produção!

## 📁 Estrutura do Projeto

```
DroneCore/
├── dronecore-dashboard-ui/     # Frontend React
│   ├── src/
│   │   ├── components/         # Componentes reutilizáveis
│   │   ├── pages/             # Páginas da aplicação
│   │   ├── contexts/          # Contextos React
│   │   ├── services/          # Serviços de API
│   │   └── utils/             # Utilitários
│   └── public/                # Arquivos estáticos
├── server/                    # Backend Node.js
│   ├── prisma/               # Schema e migrações
│   ├── index.js              # Servidor principal
│   └── init-db.js            # Script de inicialização
├── deploy.sh                 # Script de deploy automatizado
├── DEPLOY_GUIDE.md           # Guia completo de deploy
└── README.md                 # Este arquivo
```

## 🔧 Comandos Úteis

### Desenvolvimento
```bash
# Backend
cd server
npm run dev          # Desenvolvimento com nodemon
npm start            # Produção

# Frontend
cd dronecore-dashboard-ui
npm run dev          # Desenvolvimento
npm run build        # Build para produção
```

### Banco de Dados
```bash
cd server
npm run prisma:generate    # Gerar cliente Prisma
npm run prisma:migrate     # Executar migrações
npm run prisma:init        # Inicializar dados
npx prisma studio          # Interface visual do banco
```

## 🎨 Personalização

### Temas
O sistema usa Tailwind CSS e pode ser facilmente personalizado editando:
- `dronecore-dashboard-ui/tailwind.config.ts`
- `dronecore-dashboard-ui/src/index.css`

### Componentes
Todos os componentes estão em `dronecore-dashboard-ui/src/components/` e podem ser modificados conforme necessário.

## 🔒 Segurança

- Autenticação JWT
- Senhas criptografadas com bcrypt
- CORS configurado
- Validação de dados
- Rate limiting (recomendado para produção)

## 📊 Monitoramento

### Logs
- Railway: Dashboard com logs em tempo real
- Vercel: Logs de função e build

### Métricas
- Uptime monitoring
- Performance tracking
- Error tracking

## 🆘 Suporte

### Problemas Comuns

1. **Erro de conexão com banco**
   - Verifique a string de conexão
   - Confirme se o banco está ativo

2. **Erro de CORS**
   - Configure corretamente o CORS no backend
   - Verifique as URLs permitidas

3. **Erro de build**
   - Verifique se todas as dependências estão instaladas
   - Confirme a versão do Node.js

### Comandos de Debug
```bash
# Verificar logs do Railway
railway logs

# Verificar logs do Vercel
vercel logs

# Testar conexão com banco
npx prisma db pull

# Resetar banco (cuidado!)
npx prisma migrate reset
```

## 🤝 Contribuição

1. Faça um fork do projeto
2. Crie uma branch para sua feature
3. Commit suas mudanças
4. Push para a branch
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.

## 🎯 Roadmap

- [ ] Sistema de notificações
- [ ] App mobile
- [ ] Integração com APIs de clima
- [ ] Sistema de backup automático
- [ ] Relatórios avançados
- [ ] Integração com sistemas de pagamento
- [ ] Módulo de manutenção de equipamentos

---

**🚁 DroneCore** - Transformando a gestão de empresas de drone!

Para mais informações, consulte o [Guia de Deploy](DEPLOY_GUIDE.md). #   S i s t e m a - T P  
 #   S i s t e m a - T P  
 #   S i s t e m a - T P  
 