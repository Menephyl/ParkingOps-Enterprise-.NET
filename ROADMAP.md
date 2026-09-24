# ParkingOps Enterprise .NET — Roadmap de Guerra

Objetivo: sair do zero/revisão em C# e ADO.NET e construir um projeto prático alinhado à vaga, cobrindo API em C#, EF Core, ADO.NET, Dapper, SQL/T-SQL, React, Angular, Azure/AWS, CI/CD, Docker, Kubernetes, observabilidade, SRE e sustentação.

> Regra do projeto: aprender implementando. Cada etapa deve gerar código, commit e algo explicável em entrevista.

## Fase 0 — Preparação do ambiente
- Instalar/validar .NET SDK, Visual Studio ou VS Code, Git e Docker Desktop.
- Instalar SQL Server Developer/Express ou usar SQL Server em container.
- Validar `dotnet --version`, `docker --version` e conexão com o banco.
- Criar solução `ParkingOps.sln`.
- Criar projetos: Api, Domain, Application, Infrastructure e Tests.
- Entender o papel de cada camada.

**Entrega:** solução .NET compilando e primeiro endpoint `GET /health`.

## Fase 1 — C# do zero/revisão
- Tipos, variáveis e operadores.
- Condicionais e loops.
- Métodos.
- Classes, objetos, propriedades e construtores.
- Encapsulamento.
- Herança, interfaces e polimorfismo.
- Collections: List, Dictionary, HashSet.
- LINQ.
- Exceptions.
- Async/await e Task.
- Nullable reference types.
- Records e enums.
- Dependency Injection: conceito inicial.

**Prática ParkingOps:** modelar Vehicle, Stay, User, PricingRule e enums.

**Entrega:** domínio compilando + testes simples.

## Fase 2 — ASP.NET Core e APIs
- Estrutura de uma Web API.
- Controllers.
- Routing.
- DTOs.
- Model binding.
- Status codes.
- Validation.
- Dependency Injection.
- Middleware.
- Swagger/OpenAPI.
- Tratamento global de erros.
- CancellationToken.

**Endpoints iniciais:**
- `POST /api/vehicles`
- `GET /api/vehicles`
- `POST /api/stays/entry`
- `POST /api/stays/{id}/exit`
- `GET /api/stays/active`

**Entrega:** API REST funcional primeiro em memória.

## Fase 3 — SQL Server, DDL, DML e T-SQL
- Modelagem relacional.
- PK, FK, UNIQUE e NOT NULL.
- Normalização básica.
- DDL: CREATE, ALTER, DROP.
- DML: SELECT, INSERT, UPDATE, DELETE.
- JOINs.
- GROUP BY e HAVING.
- CTE.
- Views.
- Índices.
- Transactions.
- Stored Procedures.
- T-SQL e funções importantes.

**Prática:** criar schema do ParkingOps manualmente antes do ORM.

**Entrega:** pasta `database/` com scripts DDL/DML e consultas de dashboard.

## Fase 4 — EF Core
- DbContext.
- DbSet.
- Mapeamento de entidades.
- Fluent API.
- Migrations.
- Relationships.
- Tracking e AsNoTracking.
- LINQ para SQL.
- SaveChangesAsync.
- Transactions.
- Índices e constraints.
- Evitar N+1 e consultas desnecessárias.

**Uso no projeto:** CRUD e operações transacionais principais.

**Entrega:** API persistindo Vehicle e Stay no SQL Server com EF Core.

## Fase 5 — ADO.NET do zero
- O que é ADO.NET.
- Connection string.
- SqlConnection.
- SqlCommand.
- SqlParameter.
- ExecuteNonQueryAsync.
- ExecuteScalarAsync.
- SqlDataReader.
- Transactions.
- Using/await using.
- SQL Injection e queries parametrizadas.
- Diferença entre ADO.NET, EF Core e Dapper.

**Uso no projeto:** repository específico implementado com ADO.NET puro.

**Entrega:** endpoint/consulta funcionando sem ORM.

## Fase 6 — Dapper
- Instalação e configuração.
- QueryAsync.
- QuerySingleAsync.
- ExecuteAsync.
- Parâmetros.
- Multi-mapping.
- Transactions.
- Quando preferir Dapper.

**Uso no projeto:** dashboard e relatórios.

**Entrega:** dashboard com faturamento, entradas, saídas e veículos ativos usando Dapper.

## Fase 7 — Regras de negócio do ParkingOps
- Entrada de veículo.
- Impedir duas estadias ativas para a mesma placa.
- Saída de veículo.
- Cálculo de permanência.
- Tarifa e tolerância configurável.
- Histórico de tarifa.
- Usuários Admin/Operator.
- Registro do operador de entrada e saída.
- Dashboard diário.

**Entrega:** MVP backend completo.

## Fase 8 — Testes e qualidade
- xUnit.
- Unit tests.
- Integration tests.
- Testes de services.
- Testes de regras de cobrança.
- Testes de API.
- Mocking apenas quando fizer sentido.
- Logging estruturado.
- Analyzers e formatação.

**Entrega:** suíte de testes cobrindo as regras críticas.

## Fase 9 — React + TypeScript
- Consumir API .NET.
- Login.
- Dashboard.
- Veículos.
- Entrada/saída.
- Configurações de preço.
- Axios.
- React Hook Form.
- Zod.
- Tratamento de erros e loading.

**Entrega:** frontend principal em React integrado à API.

## Fase 10 — Angular essencial
- Angular CLI.
- Components.
- Services.
- Dependency Injection.
- Routing.
- HttpClient.
- Interfaces.
- RxJS/Observable.
- Forms.

**Prática:** mini painel de sustentação consumindo a mesma API.

**Entrega:** pequeno frontend Angular funcional, sem tentar duplicar todo o React.

## Fase 11 — Docker
- Imagem vs container.
- Dockerfile da API.
- Dockerfile do frontend.
- Volumes.
- Networks.
- Environment variables.
- Docker Compose.
- SQL Server em container.

**Entrega:** `docker compose up` sobe API + banco + frontend.

## Fase 12 — CI/CD e Azure DevOps Pipelines
- Conceito de CI e CD.
- YAML.
- Restore.
- Build.
- Test.
- Publish.
- Docker build.
- Artefatos.
- Variáveis e secrets.
- Ambientes.
- Pipeline de deploy.

**Entrega:** `azure-pipelines.yml` executando build e testes.

## Fase 13 — Azure
- Azure Storage.
- Blob Storage.
- Queue Storage.
- App Service/Container Apps: visão prática.
- Azure SQL: visão geral.
- Application Insights.
- Key Vault: conceito.
- Managed Identity: conceito.

**Prática:** ao finalizar uma estadia, publicar evento na Queue e gerar comprovante/relatório armazenado em Blob.

**Entrega:** integração real com Blob e Queue.

## Fase 14 — AWS essencial
- Comparar serviços equivalentes Azure/AWS.
- S3.
- SQS.
- ECS/EKS: visão geral.
- CloudWatch.
- IAM: fundamentos.

**Entrega:** documentação arquitetural mostrando equivalências Azure x AWS.

## Fase 15 — Kubernetes
- Pod.
- Deployment.
- ReplicaSet.
- Service.
- ConfigMap.
- Secret.
- Ingress.
- Liveness/readiness probes.
- Requests/limits.
- kubectl.

**Entrega:** manifests da API para Kubernetes.

## Fase 16 — Observabilidade, SRE e sustentação
- Logs.
- Metrics.
- Traces.
- OpenTelemetry.
- Correlation/Trace ID.
- Health checks.
- Latência, taxa de erro e disponibilidade.
- Incidentes.
- Diagnóstico de HTTP 500.
- Dependências indisponíveis.
- Timeout e retry.
- Post-mortem simples.

**Entrega:** API instrumentada + laboratório de incidente e troubleshooting.

## Fase 17 — .NET Framework legado
- Diferença entre .NET moderno e .NET Framework.
- ASP.NET Web API clássico.
- web.config.
- ADO.NET em sistema legado.
- IIS.
- Conceitos de manutenção/migração.

**Entrega:** laboratório pequeno separado para saber conversar sobre sustentação de legado.

## Fase 18 — Preparação para entrevista
- Explicar a arquitetura do ParkingOps em 3 minutos.
- Explicar EF Core vs Dapper vs ADO.NET.
- Escrever DDL e DML sem consulta.
- Explicar uma API REST.
- Explicar DI.
- Explicar async/await.
- Explicar pipeline CI/CD.
- Explicar Docker e Kubernetes.
- Explicar logs, métricas e traces.
- Resolver cenário de produção com erro 500.
- Explicar Azure Blob/Queue.
- Ser transparente sobre tempo profissional de C#/.NET.

**Entrega:** simulação técnica completa.

---

# Ordem de prioridade para a vaga

## Prioridade A — dominar primeiro
1. C#.
2. ASP.NET Core Web API.
3. SQL Server + DDL/DML/T-SQL.
4. EF Core.
5. ADO.NET.
6. Dapper.
7. React/TypeScript.

## Prioridade B — conseguir explicar e demonstrar
8. Docker.
9. CI/CD / Azure Pipelines.
10. Azure Storage.
11. Observabilidade/SRE.
12. Kubernetes.

## Prioridade C — depois da base
13. Angular.
14. AWS.
15. .NET Framework legado.

# Método de estudo
Para cada tópico:
1. Explicação curta.
2. Exemplo mínimo.
3. Você implementa.
4. Eu reviso.
5. Corrigimos juntos.
6. Criamos teste.
7. Fazemos commit.
8. Você explica com suas palavras como se estivesse na entrevista.

# Regra de ouro
Não decorar tecnologia para a entrevista. Construir, quebrar, corrigir e conseguir explicar o motivo de cada decisão.
