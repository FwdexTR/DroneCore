FROM node:18-alpine

WORKDIR /app

# Copiar arquivos de dependências
COPY package*.json ./

# Instalar dependências
RUN npm ci

# Copiar código fonte
COPY . .

# Expor porta
EXPOSE 5173

# Comando padrão
CMD ["npm", "run", "dev", "--", "--host", "0.0.0.0"] 