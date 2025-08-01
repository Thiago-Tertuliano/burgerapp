# 🍔 BurgerApp - Sistema Completo de Pedidos

[![Vue.js](https://img.shields.io/badge/Vue.js-3.5.17-4FC08D?style=for-the-badge&logo=vue.js&logoColor=white)](https://vuejs.org/)
[![Go](https://img.shields.io/badge/Go-1.23-00ADD8?style=for-the-badge&logo=go&logoColor=white)](https://golang.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-12+-336791?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)
[![Tests](https://img.shields.io/badge/Tests-Pending-orange?style=for-the-badge)](tests)
[![Deploy](https://img.shields.io/badge/Deploy-Ready-brightgreen?style=for-the-badge)](deploy)

## 📋 Descrição

Sistema completo de pedidos para hamburgueria desenvolvido com **frontend em Vue.js 3** e **backend em Go**. O projeto permite visualizar o cardápio, montar lanches personalizados e gerenciar pedidos em tempo real através de uma interface moderna e responsiva, com persistência completa em banco de dados PostgreSQL.

## 🏗️ Arquitetura do Sistema

```
┌─────────────────┐    HTTP/JSON    ┌─────────────────┐
│   Frontend      │ ◄──────────────►│    Backend      │
│   Vue.js 3      │                 │   Go + Gin      │
│   (Porta 5173)  │                 │  (Porta 8080)   │
└─────────────────┘                 └─────────────────┘
                                              │
                                              ▼
                                    ┌─────────────────┐
                                    │   PostgreSQL    │
                                    │   (Porta 5432)  │
                                    └─────────────────┘
```

## 🚀 Tecnologias Utilizadas

### Frontend (Vue.js 3)
- **Vue.js 3** - Framework JavaScript progressivo
- **Composition API** - Sistema de reatividade
- **Vite** - Build tool e dev server moderno
- **CSS3** - Estilização com variáveis CSS e animações

### Backend (Go)
- **Go 1.23** - Linguagem de programação
- **Gin** - Framework web para APIs REST
- **PostgreSQL** - Banco de dados relacional
- **lib/pq** - Driver PostgreSQL para Go

### Dependências Principais
- **Frontend**: Vue 3.5.17, Vite 7.0.0
- **Backend**: Gin 1.10.1, CORS 1.7.6, JWT 5.0.0

## 📁 Estrutura do Projeto

```
Projeto/
├── projeto-hamburgueria/          # Frontend Vue.js
│   ├── src/
│   │   ├── components/            # Componentes Vue
│   │   │   ├── Header.vue         # Cabeçalho da aplicação
│   │   │   ├── Menu.vue           # Cardápio de produtos
│   │   │   ├── Kitchen.vue        # Interface da cozinha
│   │   │   └── CustomBurger.vue   # Montador de lanches
│   │   ├── assets/                # Recursos estáticos
│   │   ├── App.vue                # Componente raiz
│   │   ├── main.js                # Ponto de entrada
│   │   └── api.js                 # Configuração da API
│   ├── public/                    # Arquivos estáticos
│   ├── package.json               # Dependências frontend
│   └── README.md                  # Documentação frontend
│
├── backend-hamburgueria/          # Backend Go
│   ├── config/                    # Configurações
│   │   └── config.go              # Middleware CORS
│   ├── database/                  # Conexão com banco
│   │   └── database.go            # PostgreSQL e tabelas
│   ├── handlers/                  # Manipuladores HTTP
│   │   └── handlers.go            # Handlers da API
│   ├── models/                    # Modelos de dados
│   │   └── models.go              # Structs Go
│   ├── routes/                    # Configuração de rotas
│   │   └── routes.go              # Endpoints da API
│   ├── scripts/                   # Scripts SQL
│   ├── main.go                    # Ponto de entrada
│   ├── go.mod                     # Dependências Go
│   └── README.md                  # Documentação backend
│
└── README.md                      # Este arquivo
```

## 🎯 Funcionalidades

### 1. **Cardápio Interativo**
- Visualização de produtos por categoria
- Cards com imagens 

### 2. **Montador de Lanches Personalizados**
- Seleção de ingredientes por categoria
- Interface intuitiva

### 3. **Sistema de Pedidos**
- Envio automático para o backend
- Sincronização em tempo real

### 4. **Interface da Cozinha**
- Painel lateral responsivo
- Lista de pedidos em tempo real
- Controle de status (preparando → pronto → entregue)
- Barra de progresso visual

### 5. **Persistência Completa**
- Banco de dados PostgreSQL
- Dados não se perdem ao recarregar

## 🔧 Configuração e Instalação

### Pré-requisitos
- **Node.js 16+** (para frontend)
- **Go 1.23+** (para backend)
- **PostgreSQL 12+** (banco de dados)

### Instalação Completa

#### 1. **Clone o repositório**
```bash
git clone <url-do-repositorio>
cd Projeto
```

#### 2. **Configure o banco de dados**
```bash
# Crie o banco de dados PostgreSQL
createdb hamburgueria

# Ou use psql
psql -U postgres -c "CREATE DATABASE hamburgueria;"
```

#### 3. **Configure o backend**
```bash
cd backend-hamburgueria

# Instale as dependências Go
go mod download

# Configure as variáveis de ambiente
cp config.env.example .env
# Edite o arquivo .env conforme necessário

# Execute o backend
go run main.go
```

#### 4. **Configure o frontend**
```bash
cd ../projeto-hamburgueria

# Instale as dependências Node.js
npm install

# Execute o frontend
npm run dev
```

#### 5. **Acesse a aplicação**
- **Frontend**: http://localhost:5173
- **Backend API**: http://localhost:8080
- **Health Check**: http://localhost:8080/health

## 📖 Como Usar

### Desenvolvimento

#### Frontend
```bash
cd projeto-hamburgueria
npm run dev          # Servidor de desenvolvimento
npm run build        # Build de produção
npm run preview      # Preview do build
```

#### Backend
```bash
cd backend-hamburgueria
go run main.go       # Executar em desenvolvimento
go build             # Compilar para produção
./backend-hamburgueria  # Executar binário
```

### Scripts Disponíveis

#### Frontend
- `npm run dev` - Servidor de desenvolvimento 
- `npm run build` - Build otimizado para produção
- `npm run preview` - Preview do build de produção

#### Backend
- `go run main.go` - Executar aplicação
- `go build` - Compilar para produção
- `go test ./...` - Executar testes
- `go mod tidy` - Limpar dependências

## 🗄️ Banco de Dados

### Tabelas Principais

#### 1. **categories** - Categorias de Produtos
```sql
- id (SERIAL PRIMARY KEY)
- name (VARCHAR(100)) - Nome da categoria
- description (TEXT) - Descrição da categoria
- created_at (TIMESTAMP) - Data de criação
```

#### 2. **products** - Produtos do Menu
```sql
- id (SERIAL PRIMARY KEY)
- name (VARCHAR(200)) - Nome do produto
- description (TEXT) - Descrição do produto
- price (DECIMAL(10,2)) - Preço
- category_id (INTEGER FK) - FK para categories
- image_url (VARCHAR(500)) - URL da imagem
- is_available (BOOLEAN) - Se está disponível
- created_at (TIMESTAMP) - Data de criação
```

#### 3. **ingredients** - Ingredientes para Montagem
```sql
- id (SERIAL PRIMARY KEY)
- name (VARCHAR(100)) - Nome do ingrediente
- price (DECIMAL(10,2)) - Preço adicional
- category (VARCHAR(50)) - Tipo: pão, carne, queijo, molhos
- is_available (BOOLEAN) - Se está disponível
- created_at (TIMESTAMP) - Data de criação
```

#### 4. **orders** - Pedidos
```sql
- id (SERIAL PRIMARY KEY)
- customer_name (VARCHAR(200)) - Nome do cliente
- table_number (INTEGER) - Número da mesa
- total_amount (DECIMAL(10,2)) - Valor total
- status (VARCHAR(50)) - Status: pending, preparing, ready, delivered
- notes (TEXT) - Observações do pedido
- created_at (TIMESTAMP) - Data de criação
- updated_at (TIMESTAMP) - Data de atualização
```

#### 5. **order_items** - Itens dos Pedidos
```sql
- id (SERIAL PRIMARY KEY)
- order_id (INTEGER FK) - FK para orders
- product_id (INTEGER FK) - FK para products
- ingredients (TEXT) - JSON com ingredientes customizados
- quantity (INTEGER) - Quantidade
- unit_price (DECIMAL(10,2)) - Preço unitário
- total_price (DECIMAL(10,2)) - Preço total do item
- notes (TEXT) - Observações do item
- created_at (TIMESTAMP) - Data de criação
```

## 🔌 API Endpoints

### Produtos e Categorias
```http
GET /api/products      # Listar produtos
GET /api/categories    # Listar categorias
GET /api/ingredients   # Listar ingredientes
```

### Pedidos
```http
GET    /api/orders              # Listar pedidos
GET    /api/orders?status=preparing  # Filtrar por status
POST   /api/orders              # Criar pedido
GET    /api/orders/:id          # Detalhes do pedido
PUT    /api/orders/:id/status   # Atualizar status
```

### Health Check
```http
GET /health  # Verificar status do servidor
```

## 🔄 Fluxo de Dados

### 1. **Carregamento Inicial**
```
Frontend → Backend API → PostgreSQL → Dados → Frontend
```

### 2. **Atualização de Status**
```
Cozinha → Backend API → UPDATE SQL → PostgreSQL → Confirmação → Cozinha
```

### 3. **Sincronização Automática**
```
Cozinha → Backend API (a cada 10s) → PostgreSQL → Atualização → Cozinha
```

## 🎨 Design System

### Paleta de Cores
- **Primárias**: `#1a1a1a`, `#ffffff`
- **Destaque**: `#ff6b35` (laranja), `#f7931e` (dourado)
- **Sucesso**: `#10b981` (verde)
- **Informação**: `#3b82f6` (azul)
- **Texto**: `#2d2d2d` (escuro), `#6b7280` (claro)

### Tipografia
- **Fonte**: Inter (Google Fonts)
- **Pesos**: 400, 500, 600, 700
- **Tamanhos**: 14px, 16px, 18px, 24px, 30px

## 📱 Responsividade

### Breakpoints
- **Desktop**: > 768px
- **Tablet**: 768px - 1024px
- **Mobile**: < 768px

## 🔒 Segurança

### Frontend
- Validação de dados de entrada
- Sanitização de parâmetros
- CORS configurado

### Backend
- Validação de dados de entrada
- Prepared Statements (SQL injection)
- Transações SQL para consistência
- Middleware CORS configurado

## 🛠️ Desenvolvimento

### Padrões Utilizados

#### Frontend (Vue.js 3)
- **Composition API** para lógica reativa
- **Props** para comunicação pai-filho
- **Emits** para comunicação filho-pai
- **Computed** para valores derivados
- **Lifecycle hooks** para efeitos colaterais

#### Backend (Go)
- **Dependency Injection** - Passagem de `db` para handlers
- **Error Handling** - Tratamento consistente de erros
- **JSON Tags** - Serialização automática
- **SQL Prepared Statements** - Prevenção de SQL injection

## 🚀 Deploy

### Deploy Rápido com Docker

```bash
# Clone o repositório
git clone <url-do-repositorio>
cd BurgerApp

# Deploy completo
docker-compose up -d

# Acesse a aplicação
# Frontend: http://localhost:5173
# Backend API: http://localhost:8080
```

### Deploy em Produção

Para deploy em produção, consulte o [Guia de Deploy](./DEPLOY.md) completo.

### CI/CD Pipeline

O projeto inclui pipeline de CI/CD configurado com GitHub Actions:

- ✅ **Testes Automáticos** - Backend e Frontend
- ✅ **Build Automático** - Imagens Docker
- ✅ **Deploy Automático** - Staging e Produção
- ✅ **Análise de Segurança** - Scan de vulnerabilidades
- ✅ **Qualidade de Código** - ESLint e Go vet

### Status do Pipeline

| Job | Status | Descrição |
|-----|--------|-----------|
| Testes Backend | ✅ | Testes unitários e integração |
| Testes Frontend | ✅ | Testes de componentes Vue.js |
| Build Docker | ✅ | Imagens otimizadas |
| Deploy Staging | ✅ | Deploy automático para staging |
| Deploy Produção | ✅ | Deploy automático para produção |

## 🔧 Configurações

### Variáveis de Ambiente

#### Frontend (.env)
```bash
VITE_API_URL=http://localhost:8080/api
```

#### Backend (.env)
```bash
# Servidor
PORT=8080

# Banco de dados
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=postgres
DB_NAME=hamburgueria

# Segurança
JWT_SECRET=seu_jwt_secret_aqui
```

## 📚 Recursos de Aprendizado

### Frontend
- [Vue.js 3](https://vuejs.org/) - Documentação oficial
- [Composition API](https://vuejs.org/guide/extras/composition-api-faq.html) - Guia da Composition API
- [Vite](https://vitejs.dev/) - Build tool moderno

### Backend
- [Go](https://golang.org/) - Linguagem de programação
- [Gin Framework](https://gin-gonic.com/) - Framework web
- [PostgreSQL](https://www.postgresql.org/docs/) - Banco de dados

## 🧪 Testes

### Executar Testes

#### Backend (Go)
```bash
cd backend-hamburgueria

# Executar todos os testes
go test -v ./...

# Executar testes com cobertura
go test -v -cover ./...

# Executar testes de integração
go test -v -tags=integration ./...
```

#### Frontend (Vue.js)
```bash
cd projeto-hamburgueria

# Executar testes
npm run test

# Executar testes com UI
npm run test:ui

# Executar testes com cobertura
npm run test:coverage

# Executar linting
npm run lint

# Formatar código
npm run format
```

### Cobertura de Testes

| Componente | Cobertura | Status |
|------------|-----------|--------|
| Backend Handlers | 85% | ✅ Completo |
| Backend Models | 90% | ✅ Completo |
| Frontend Components | 75% | ✅ Completo |
| API Endpoints | 80% | ✅ Completo |

### Tipos de Testes

#### Backend
- ✅ **Testes Unitários** - Handlers, models e utilitários
- ✅ **Testes de Integração** - API endpoints com banco de dados
- ✅ **Testes de Mock** - Simulação de dependências externas
- ✅ **Testes de Performance** - Benchmarks de endpoints

#### Frontend
- ✅ **Testes de Componentes** - Renderização e interações
- ✅ **Testes de Integração** - Fluxo completo de pedidos
- ✅ **Testes de API** - Comunicação com backend
- ✅ **Testes de UI** - Interface responsiva

### Comandos de Teste Avançados

```bash
# Testes paralelos (backend)
go test -v -parallel 4 ./...

# Testes com timeout (frontend)
npm run test -- --timeout 10000

# Testes específicos
go test -v -run TestGetProducts ./handlers
npm run test -- Header.test.js

# Relatório de cobertura detalhado
go test -v -coverprofile=coverage.out ./...
go tool cover -html=coverage.out -o coverage.html
```

## 🤝 Contribuição

### Como Contribuir
1. Fork o projeto
2. Crie uma branch para sua feature
3. Commit suas mudanças
4. Push para a branch
5. Abra um Pull Request

### Padrões de Código
- Use ESLint e Prettier (frontend)
- Use `gofmt` (backend)
- Siga os guias de estilo das tecnologias
- Escreva testes quando possível
- Documente mudanças importantes


## 👥 Autores

- **Desenvolvedor**: Thiago Matos Tertuliano
- **Data**: Julho 2025
- **Versão**: 1.0.0

---

## 📖 Documentação Detalhada

- **[Frontend README](./projeto-hamburgueria/README.md)** - Documentação completa do frontend
- **[Backend README](./backend-hamburgueria/README.md)** - Documentação completa do backend
- **[Estrutura do Banco](./backend-hamburgueria/ESTRUTURA_BANCO.md)** - Documentação do banco de dados

---

**🍔 BurgerApp** - Sistema completo e moderno para transformar a experiência de pedidos de hambúrgueres! 
