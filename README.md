# 🥏 UltimateTeam

Gestão simples e moderna de times, jogadores, treinos e presenças. Login via OAuth2 (Google/GitHub), UI com Thymeleaf e PostgreSQL com migrações Flyway.

## 🚀 Stack
- ☕ Java 17 • Spring Boot 3 (Web, JPA, Validation)
- 🔐 OAuth2 Client (Google/GitHub)
- 🧩 Thymeleaf (+ java8time)
- 🐘 PostgreSQL • 🐦 Flyway
- 📦 Gradle • 🐳 Docker/Compose

## 🛠️ Pré‑requisitos
- Java 17+
- (Opcional) Docker + Docker Compose
- Credenciais OAuth2: `GITHUB_*` e/ou `GOOGLE_*`

## ⚙️ Configuração rápida
- Perfil ativo: `ACTIVE_PROFILE` (padrão `dev`)
- Em `prod`, banco via `application-prod.properties` usando variáveis:
  - `DB_URL` • `DB_USER` • `DB_PASS`

Exemplo `.env`:
```env
ACTIVE_PROFILE=prod
DB_URL=jdbc:postgresql://localhost:5432/ultimateteam
DB_USER=ultimateteam
DB_PASS=ultimateteam
GITHUB_CLIENT_ID=xxxx
GITHUB_CLIENT_SECRET=xxxx
GOOGLE_CLIENT_ID=xxxx
GOOGLE_CLIENT_SECRET=xxxx
```

## 🐘 Banco com Compose (opcional)
```bash
docker compose up -d
```
Cria `ultimateteam` em `localhost:5432` (user/senha `ultimateteam`).

## ▶️ Rodando a aplicação (dev)
```bash
./gradlew bootRun
```
Acesse: `http://localhost:8080`

## 📦 Build e Docker
- JAR:
  ```bash
  ./gradlew bootJar
  ```
- Docker:
  ```bash
  docker build -t ultimateteam:latest .
  docker run --rm -p 8080:8080 \
    -e ACTIVE_PROFILE=prod \
    -e DB_URL=jdbc:postgresql://host.docker.internal:5432/ultimateteam \
    -e DB_USER=ultimateteam -e DB_PASS=ultimateteam \
    -e GITHUB_CLIENT_ID=xxxx -e GITHUB_CLIENT_SECRET=xxxx \
    -e GOOGLE_CLIENT_ID=xxxx -e GOOGLE_CLIENT_SECRET=xxxx \
    ultimateteam:latest
  ```

## ✅ Funcionalidades
- 🏟️ Times: criar/editar/visualizar
- 🧑‍🤝‍🧑 Jogadores: CRUD completo
- 🗓️ Treinos: agenda e gerenciamento
- ✅ Presenças: controle por treino
- 🔐 Login OAuth2 (Google/GitHub)
- 🌍 i18n + Templates Thymeleaf

## 🗂️ Onde encontrar
- Código: `src/main/java/br/com/fiap/ultimateteam`
- Templates: `src/main/resources/templates`
- Migrações: `src/main/resources/db/migration` (+ `db/migration-dev`)
- Config: `src/main/resources/application.properties` (+ `application-prod.properties`)