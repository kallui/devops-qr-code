FROM node:18-alpine AS base

# set wd in container
WORKDIR /app

# install dependencies
COPY package.json package-lock.json* yarn.lock* pnpm-lock.yaml* ./

RUN \
    if [ -f yarn.lock ]; then yarn --frozen-lockfile; \
    elif [ -f package-lock.json ]; then npm ci; \
    elif [ -f pnpm-lock.yaml ]; then corepack enable pnpm && pnpm install --frozen-lockfile; \
    else echo "No lock file found"; exit 1; \
    fi

# copy everything to the container
COPY . .

RUN npm run build

# expose port
EXPOSE 3000

#run app
CMD ["npm", "start"]