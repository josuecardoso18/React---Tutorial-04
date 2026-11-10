# DevFlix — React Tutorials 01 a 04

Projeto de estudo do Senac RJ. Frontend React/Vite e API NestJS com PostgreSQL, Docker Compose e Prisma.

## Estrutura
- `frontend/`: aplicação React/Vite.
- `backend/`: API NestJS, Prisma e migrations.
- `docker-compose.yml`: PostgreSQL 17.

## Requisitos
Node.js compatível com Vite, npm e Docker Desktop.

## 1. Iniciar PostgreSQL
Na raiz do projeto:
```bash
docker compose up -d
docker compose ps
```

## 2. Configurar backend
Entre em `backend` e crie `.env` a partir do exemplo:
```powershell
Copy-Item .env.example .env
```
Depois execute:
```bash
npm install
npx prisma validate
npx prisma migrate dev
npx prisma generate
npx prisma db seed
npm run start:dev
```

A API utiliza prefixo `/api` neste projeto:
- `GET http://localhost:3000/api/health`
- `GET http://localhost:3000/api/categories`
- `GET http://localhost:3000/api/courses`
- `GET http://localhost:3000/api/courses/1`

## 3. Frontend
Em outro terminal:
```bash
cd frontend
npm install
npm run dev
```
Abra o endereço local mostrado pelo Vite (normalmente http://localhost:5173).

## Tutorial 04
O schema inclui `Category`, `Course` e `Lesson`. A migration `add_courses_lessons` é incremental e preserva os registros de Category. O seed utiliza `upsert`, então pode ser executado novamente sem duplicar os registros correspondentes.

**Importante:** não publique o arquivo `.env`. Use `.env.example` apenas como modelo local.
