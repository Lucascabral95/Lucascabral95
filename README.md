<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=soft&color=0:2F81F7,100:1a1b27&height=180&section=header&text=Lucas%20Cabral&fontSize=60&fontColor=fff&fontAlignY=38&desc=Software%20Engineer%20%7C%20Backend%20-%20Cloud%20Computing%20%7C%20DevOps%20&descAlignY=65&descSize=18" alt="Header"/>
</div>

<div align="center">

 [![Typing SVG](https://readme-typing-svg.herokuapp.com?font=Fira+Code&pause=1000&color=2F81F7&center=true&vCenter=true&width=650&lines=Go+%7C+NestJS+%7C+AWS+ECS+Fargate+%7C+Terraform;Microservicios+%7C+Database+per+Service;Observabilidad%3A+Prometheus+%2B+Loki+%2B+Grafana+Cloud;Event-Driven%3A+SNS+%2B+SQS+%2B+Lambda;Infraestructura+como+c%C3%B3digo%2C+siempre)](https://git.io/typing-svg)

  <a href="https://github.com/Lucascabral95">
    <img src="https://img.shields.io/github/followers/Lucascabral95?label=Seguidores&style=for-the-badge&color=2F81F7" alt="GitHub Followers" />
  </a>
  <a href="https://linkedin.com/in/lucas-gaston-cabral">
    <img src="https://img.shields.io/badge/LinkedIn-Conectar-0077B5?style=for-the-badge&logo=linkedin" alt="LinkedIn" />
  </a>
  <a href="mailto:Lucassimple@hotmail.com">
    <img src="https://img.shields.io/badge/Email-Contacto-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" />
  </a>

  📍 Tigre, Buenos Aires, Argentina | 🌐 [Portfolio](https://bit.ly/47unnek)

</div>

---

## 👨‍💻 Sobre Mí

Software Engineer con especialización en **Cloud Computing** y **Arquitecturas Distribuidas**. Mi enfoque combina desarrollo de software escalable con principios de DevOps y Site Reliability Engineering (SRE).

```typescript
const lucas = {
    rol: "Software Engineer",
    ubicacion: "Buenos Aires, Argentina",
    especialidades: ["Arquitectura Cloud", "Microservicios", "Sistemas Event-Driven"],
    enfoqueActual: "Construyendo sistemas distribuidos resilientes en AWS",
    certificaciones: ["AWS Developer Associate", "Cisco Cybersecurity Analyst"],
    filosofia: "Clean Code + Automatización + Aprendizaje Continuo"
};
```

### 🎯 Competencias Principales

- **Ingeniería Backend:** Diseño de microservicios escalables con NestJS, Go y Node.js
- **Infraestructura Cloud:** Arquitectura serverless y contenerizada en AWS (ECS, Lambda, Fargate)
- **DevOps & IaC:** Automatización con Terraform, Docker, Kubernetes y pipelines CI/CD
- **Observabilidad & Monitoreo:** Métricas con Prometheus, dashboards con Grafana (Cloud + local), agregación de logs con Loki y alerting con Alertmanager
- **Desarrollo Frontend:** SPAs modernas con React, Next.js y Angular
- **Diseño de Bases de Datos:** PostgreSQL, MongoDB, Redis, DynamoDB (SQL & NoSQL)
- **Seguridad & Autenticación:** Implementación de OAuth2, JWT, AWS Cognito

---

## 🏗️ Ejemplo de Arquitectura: Microservicios en Producción

Este diagrama representa el tipo de arquitectura distribuida que diseño e implemento: microservicios con aislamiento de datos, mensajería asíncrona y stack de observabilidad completo en producción.

```mermaid
graph TB
    subgraph "Client Layer"
        A[Web Client\nNext.js] 
        B[Mobile App]
    end

    subgraph "Edge & Gateway"
        C[CloudFront CDN]
        D[API Gateway\nRouting + Rate Limit]
        E[Auth Service\nNestJS + JWT + Cognito]
    end

    subgraph "Microservices — ECS Fargate"
        F[User Service\nNestJS]
        G[Product Service\nGo + Gin]
        H[Order Service\nNestJS]
        I[Payment Service\nGo + Gin]
        J[Notification Service\nNode.js]
    end

    subgraph "Async Messaging — Event Bus"
        K{SNS Topic\norder.events}
        L[SQS Queue\nPayments]
        M[SQS Queue\nNotifications]
        N[Lambda\nPayment Worker]
        O[Lambda\nEmail Worker]
    end

    subgraph "Data Layer — DB per Service"
        P[(Users DB\nRDS PostgreSQL)]
        Q[(Products DB\nRDS PostgreSQL)]
        R[(Orders DB\nRDS PostgreSQL)]
        S[(Transactions\nDynamoDB)]
        T[(Cache\nElastiCache Redis)]
    end

    subgraph "Observability Stack"
        U[Prometheus\nMetrics Scrape]
        V[Promtail\nLog Collector]
        W[Loki\nLog Aggregation]
        X[Alertmanager\nRouting + Silencing]
        Y[Grafana Cloud\nDashboards + Alerts]
    end

    subgraph "Alerting Channels"
        Z[Slack]
        AA[PagerDuty]
        AB[Email]
    end

    A & B --> C --> D
    D --> E
    E --> F & G & H & I
    H --> K
    K --> L --> N --> S
    K --> M --> O
    N --> I
    F --> P
    G --> Q & T
    H --> R
    I --> S

    F & G & H & I & J -->|/metrics| U
    F & G & H & I & J -->|stdout logs| V
    V --> W
    U -->|remote_write| Y
    W -->|LogQL| Y
    U --> X
    X --> Z & AA & AB

    style C fill:#FF9900,color:#fff
    style D fill:#FF9900,color:#fff
    style K fill:#FF9900,color:#fff
    style L fill:#FF9900,color:#fff
    style M fill:#FF9900,color:#fff
    style N fill:#FF9900,color:#fff
    style O fill:#FF9900,color:#fff
    style E fill:#68BC00,color:#fff
    style F fill:#68BC00,color:#fff
    style H fill:#68BC00,color:#fff
    style J fill:#68BC00,color:#fff
    style G fill:#00ADD8,color:#fff
    style I fill:#00ADD8,color:#fff
    style P fill:#336791,color:#fff
    style Q fill:#336791,color:#fff
    style R fill:#336791,color:#fff
    style S fill:#4053D6,color:#fff
    style T fill:#DC382D,color:#fff
    style U fill:#E6522C,color:#fff
    style V fill:#F5A623,color:#fff
    style W fill:#F5A623,color:#fff
    style X fill:#E6522C,color:#fff
    style Y fill:#F46800,color:#fff
```

> **Decisiones de diseño clave:**
> - 🔒 **Database per service** — aislamiento total, sin shared schema
> - ⚡ **Comunicación asíncrona** vía SNS/SQS para operaciones no bloqueantes (pagos, notificaciones)
> - 📊 **Observabilidad de tres pilares**: métricas (Prometheus), logs (Loki + Promtail) y dashboards unificados (Grafana Cloud)
> - 🚨 **Alertmanager** con routing por severidad hacia Slack, PagerDuty y Email
> - 🏗️ **IaC con Terraform** para toda la infraestructura AWS — reproducible y versionado

---

## 💼 Logros Profesionales

### 🚀 Logros Clave

| Desafío | Solución | Impacto |
|---------|----------|---------|
| **Alta Latencia en API** | Implementación de caché multinivel (L1 In-Memory + L2 Redis Cluster) y optimización de queries SQL | **30% de reducción** en latencia p95 |
| **Fallas en Despliegues** | Diseño de pipeline CI/CD con infraestructura inmutable usando GitHub Actions & Terraform | Despliegues **Blue/Green sin downtime** |
| **Cuellos de Botella** | Migración de monolito a arquitectura asíncrona usando RabbitMQ/SQS para procesamiento en segundo plano | **+200% de throughput** (RPS) |
| **Procesamiento de Pagos** | Sistema de transacciones event-driven con integración Stripe/MercadoPago | Procesamiento **asíncrono y seguro** |
| **Cero Visibilidad en Producción** | Stack completo: Prometheus (métricas p95/p99, RPS, goroutines), Loki + Promtail (logs) y Grafana Cloud con `remote_write` | **Detección proactiva** de anomalías con alerting automático vía Alertmanager |
| **Escalabilidad bajo picos de tráfico** | Infraestructura auto-escalable en AWS ECS Fargate con ALB, Auto Scaling por métricas CPU/memoria en CloudWatch, VPC con subnets privadas/públicas, Security Groups con mínimo privilegio e IAM roles por servicio | **0 downtime** bajo picos de carga, escalado automático en menos de **90 segundos** y superficie de ataque minimizada |

### 🛠️ Experiencia en Producción

**Software Engineer Freelance** | *Enero 2024 - Actualidad*

- ☁️ **Arquitectura Cloud:** Diseño de infraestructura serverless y contenerizada en AWS (ECS Fargate, Lambda) usando Terraform (IaC)
- 🔧 **Sistemas Backend:** Desarrollo de microservicios event-driven con NestJS y Go, integrando pasarelas de pago (Stripe, MercadoPago) y colas de mensajes (RabbitMQ, SQS)
- ⚡ **Optimización de Rendimiento:** Reducción del 30% en latencia mediante estrategias de caching y ajuste avanzado de queries en PostgreSQL/MongoDB
- 🧪 **Aseguramiento de Calidad:** Implementación de suites de testing completas (Unit, Integration, E2E) con Jest y React Testing Library, manteniendo +80% de cobertura de código
- 🔐 **Implementación de Seguridad:** Construcción de esquemas robustos de autenticación con AWS Cognito, OAuth2, JWT y Firebase Auth
- 📊 **Observabilidad en Producción:** Implementación del stack completo de monitoreo con Prometheus, Grafana Cloud y Loki — dashboards con métricas p95/p99, agregación de logs con Promtail y alerting con Alertmanager

---

## 🛠️ Stack Tecnológico

### Lenguajes & Frameworks

<div align="center">

<table>
<tr>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=ts" width="50" height="50" alt="TypeScript" />
<br><strong>TypeScript</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=go" width="50" height="50" alt="Go" />
<br><strong>Golang</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=nodejs" width="50" height="50" alt="Node.js" />
<br><strong>Node.js</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=python" width="50" height="50" alt="Python" />
<br><strong>Python</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=nestjs" width="50" height="50" alt="NestJS" />
<br><strong>NestJS</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=express" width="50" height="50" alt="Express" />
<br><strong>Express</strong>
</td>
<td align="center" width="100">
<img src="https://raw.githubusercontent.com/gin-gonic/logo/master/color.png" width="50" height="50" alt="Gin" />
<br><strong>Gin</strong>
</td>
</tr>
</table>

</div>

### Tecnologías Frontend

<div align="center">

<table>
<tr>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=react" width="50" height="50" alt="React" />
<br><strong>React</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=nextjs" width="50" height="50" alt="Next.js" />
<br><strong>Next.js</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=angular" width="50" height="50" alt="Angular" />
<br><strong>Angular</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=tailwind" width="50" height="50" alt="Tailwind" />
<br><strong>Tailwind</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=graphql" width="50" height="50" alt="GraphQL" />
<br><strong>GraphQL</strong>
</td>
</tr>
</table>

</div>

### Cloud & DevOps

<div align="center">

<table>
<tr>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=aws" width="50" height="50" alt="AWS" />
<br><strong>AWS</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=docker" width="50" height="50" alt="Docker" />
<br><strong>Docker</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=kubernetes" width="50" height="50" alt="Kubernetes" />
<br><strong>Kubernetes</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=terraform" width="50" height="50" alt="Terraform" />
<br><strong>Terraform</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=github" width="50" height="50" alt="GitHub Actions" />
<br><strong>GH Actions</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=jenkins" width="50" height="50" alt="Jenkins" />
<br><strong>Jenkins</strong>
</td>
<td align="center" width="100">
<img src="https://raw.githubusercontent.com/grafana/grafana/main/public/img/grafana_icon.svg" width="50" height="50" alt="Grafana" />
<br><strong>Grafana</strong>
</td>
<td align="center" width="100">
<img src="https://raw.githubusercontent.com/grafana/loki/main/docs/sources/logo.png" width="50" height="50" alt="Loki" />
<br><strong>Loki</strong>
</td>
</tr>
</table>

</div>

### Bases de Datos & Caching

<div align="center">

<table>
<tr>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=postgresql" width="50" height="50" alt="PostgreSQL" />
<br><strong>PostgreSQL</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=mongodb" width="50" height="50" alt="MongoDB" />
<br><strong>MongoDB</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=redis" width="50" height="50" alt="Redis" />
<br><strong>Redis</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=dynamodb" width="50" height="50" alt="DynamoDB" />
<br><strong>DynamoDB</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=mysql" width="50" height="50" alt="MySQL" />
<br><strong>MySQL</strong>
</td>
<td align="center" width="100">
<img src="https://skillicons.dev/icons?i=firebase" width="50" height="50" alt="Firebase" />
<br><strong>Firebase</strong>
</td>
</tr>
</table>

</div>

### Experiencia en Servicios AWS

```yaml
Cómputo & Orquestación:
  - AWS Lambda (Serverless)
  - Amazon ECS & Fargate (Contenedores)
  - Elastic Beanstalk
  - AWS Step Functions

Mensajería & Eventos:
  - Amazon SQS (Colas)
  - Amazon SNS (Pub/Sub)
  - Arquitectura Event-Driven

Datos & Almacenamiento:
  - Amazon RDS (PostgreSQL/MySQL)
  - Amazon DynamoDB
  - Amazon ElastiCache (Redis)
  - Amazon S3

Redes & Seguridad:
  - Amazon VPC
  - AWS Cognito
  - Políticas IAM
  - CloudFront CDN

DevOps & Monitoreo:
  - AWS CodePipeline
  - AWS CodeCommit
  - CloudWatch Logs & Metrics
  - X-Ray (Tracing)
```

---

<div align="center">
  <h2 style="color: #2F81F7;">📊 Estadísticas de GitHub</h2>
</div>

<div align="center">
  <img src="https://github-readme-stats-sigma-five.vercel.app/api?username=Lucascabral95&show_icons=true&theme=tokyonight&hide_border=true" height="180" alt="Stats" />
  <img src="https://github-readme-stats-sigma-five.vercel.app/api/top-langs/?username=Lucascabral95&layout=compact&theme=tokyonight&hide_border=true" height="180" alt="Languages" />
</div>

<div align="center">
  <img src="https://streak-stats.demolab.com?user=Lucascabral95&theme=react&hide_border=true&background=0D1117&ring=2F81F7&fire=2F81F7&currStreakLabel=2F81F7&sideLabels=2F81F7&dates=9CA3AF" alt="Racha de GitHub" width="500"/>
</div>

<div align="center">
  <h3 style="color: #2F81F7;">Gráfico de Actividad</h3>
</div>

<div align="center">
  <img src="https://ghchart.rshah.org/2F81F7/Lucascabral95" alt="Gráfico de Contribuciones de GitHub" width="800"/>
</div>

<div align="center">
  <h3 style="color: #2F81F7;">Gráfico de Contribución</h3>
</div>

<div align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=Lucascabral95&theme=react-dark&hide_border=true&bg_color=0D1117&color=2F81F7&line=2F81F7&point=FFFFFF&area=true" alt="Gráfico de Contribución" width="100%"/>
</div>

---

## 🎓 Educación & Certificaciones

<table>
<tr>
<td width="50%">

### 🎯 Certificaciones
- ☁️ **Working with Microservices in Go** (2026)
- ☁️ **Go - The complete guide** (2026)
- ☁️ **AWS Developer Associate** (2025)
- ☁️ **AWS Cloud Practitioner** (2025)
- 🔐 **Cisco Cybersecurity Analyst Junior** (2025)
- 📚 **React Native Avanzado** (Udemy, 2024)
- 🔧 **Angular Avanzado** (Udemy, 2024)
- 🔧 **NestJS Microservicios Avanzado** (Udemy, 2024)

</td>
<td width="50%">

### 🎓 Formación Académica
- 💻 **Desarrollo Full Stack** - Coderhouse (2023)
  - *Top 10 de la promoción*
- 🗄️ **SQL & Diseño de Bases de Datos** - Coderhouse (2024)

</td>
</tr>
</table>

---

## 🔥 Proyectos Destacados

### 🎫 SeatGuard: Enterprise Reservation Engine
**Stack Tecnológico:** Angular 20, Go (Gin), NestJS, PostgreSQL (Neon), AWS ECS Fargate, Lambda, SQS, Stripe, Terraform

Plataforma empresarial de microservicios con backend polyglot desplegado en AWS ECS Fargate. Implementa bloqueo de asientos en tiempo real con concurrencia optimista, procesamiento asíncrono de pagos mediante Lambda + SQS + Stripe, y arquitectura limpia siguiendo principios SOLID.

- ✅ Arquitectura de microservicios polyglot (Go + NestJS + Node.js)
- ✅ Infraestructura serverless en AWS con Terraform (IaC)
- ✅ Bloqueo de asientos en tiempo real con concurrencia optimista
- ✅ Procesamiento asíncrono event-driven con Lambda + SQS
- ✅ Frontend Angular 20 con SSR, Signals y Zoneless Change Detection
- ✅ [Demo en vivo](https://seat-guard-reservation-frontend.vercel.app/) | [Código Frontend](https://github.com/Lucascabral95/seat-guard-reservation-frontend) | [Código Backend](https://github.com/Lucascabral95/seat-guard-reservation-engine)

### 🗄️ In-Memory Database Engine: E-Commerce API
**Stack Tecnológico:** Go (Gin), PostgreSQL, GORM, JWT, Redis Protocol (RESP), Prometheus, Grafana Cloud, Docker, Terraform, AWS (EC2 + ECR + SSM)

API REST de e-commerce con arquitectura en capas (`Handler → Service → Repository`), carrito en memoria RAM con TTL de 24h y un **servidor TCP custom compatible con el protocolo Redis (RESP)** implementado desde cero. Incluye infraestructura completa en AWS con Terraform, observabilidad con Prometheus + Grafana Cloud y pipeline CI/CD con GitHub Actions.

- ✅ Servidor TCP propio compatible con comandos RESP (`PING`, `SET`, `GET`, `DEL`) compartiendo el mismo `MemoryStore` que la API HTTP
- ✅ Checkout transaccional de 6 pasos con bloqueo `FOR UPDATE`, descuento de stock y rollback automático (`409 Conflict`)
- ✅ Carrito en memoria por usuario autenticado con TTL 24h, renovado en escrituras y cleanup periódico
- ✅ Observabilidad completa: métricas p95/p99, RPS por endpoint, goroutines, heap Go y `remote_write` a Grafana Cloud
- ✅ Infraestructura IaC con Terraform (ECR + EC2 + SSM Parameter Store + IAM) y deploy automático vía GitHub Actions
- ✅ Rate limiting por IP (global `10 req/s` + estricto en auth `5 req/min`), CORS, Swagger y colección Postman incluidos
- ✅ [Código Backend](https://github.com/Lucascabral95/in-memory-database-engine)

### 🛒 Chroma - E-commerce Full Stack
**Stack Tecnológico:** Next.js, NestJS, TypeScript, PostgreSQL (Neon), Prisma, Zustand, Tailwind CSS

E-commerce moderno con gestión de productos, carrito de compras inteligente, procesamiento de pagos con MercadoPago y autenticación JWT segura. Implementa SSR para SEO, caché parametrizado avanzado con TanStack Query y UI responsive premium.

- ✅ Autenticación y autorización con roles (USER, MANAGER, ADMIN)
- ✅ Gestión completa de productos con variantes y control de stock
- ✅ Carrito de compras con persistencia y sincronización entre dispositivos
- ✅ Integración con MercadoPago para procesamiento de pagos
- ✅ Cache parametrizado avanzado con TanStack Query
- ✅ [Demo en vivo](https://frontend-ecommerce-chroma.vercel.app/) | [Código Frontend](https://github.com/Lucascabral95/frontend-ecommerce-chroma) | [Código Backend](https://github.com/Lucascabral95/ecommerce-chrome-backend)

### 🔗 Linkly - URL Shortener Platform
**Stack Tecnológico:** Angular, NestJS, TypeScript, PostgreSQL (Neon), Prisma, Socket.io, Tailwind CSS

Plataforma full-stack de acortamiento de URLs con autenticación avanzada (local + OAuth Google), analíticas en tiempo real y sistema de recuperación de contraseña seguro. Panel administrativo con gestión de usuarios, roles (ADMIN, PREMIUM, FREE) y métricas detalladas.

- ✅ Acortamiento de URLs con alias personalizados
- ✅ Protección por contraseña y expiración automática de enlaces
- ✅ Panel de analíticas en tiempo real (clics, dispositivos, geolocalización)
- ✅ Autenticación OAuth 2.0 con Google
- ✅ Sistema de recuperación de contraseña con tokens autodestructivos
- ✅ [Demo en vivo](https://links-shorteners-linky.netlify.app/) | [Código Frontend](https://github.com/Lucascabral95/links-shorteners-linkly) | [Código Backend](https://github.com/Lucascabral95/links-shorteners)

---

## 📈 Crecimiento Profesional

```typescript
const desarrollador = {
    nombre: "Lucas Cabral",
    ubicacion: "Buenos Aires, Argentina",

    dominando: [
        "Kubernetes — orquestación avanzada, Helm charts, resource limits y HPA",
        "Patrones distribuidos — SAGA, CQRS, Outbox Pattern y consistencia eventual",
        "AWS Security — IAM least privilege, KMS, Secrets Manager y GuardDuty",
        "Observabilidad avanzada — tracing distribuido con OpenTelemetry y Jaeger",
        "Performance engineering — profiling en Go, optimización de queries y connection pooling"
    ],

    proximasCertificaciones: [
        "AWS Solutions Architect Professional",
        "Certified Kubernetes Administrator (CKA)",
    ],

    principios: [
        "Infraestructura como código, siempre",
        "Observabilidad desde el día 1, no como afterthought",
        "Seguridad por diseño, no por capas",
        "Sistemas que fallan con gracia antes que sistemas que no fallan"
    ],

    buscando: "Equipos que construyan sistemas distribuidos a escala real"
};
```

---

## 🤝 Conectemos

<div align="center">

Siempre estoy abierto a discutir sobre **arquitectura cloud**, **patrones de microservicios** o **mejores prácticas de DevOps**. ¡No dudes en contactarme!

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Conectar-0077B5?style=for-the-badge&logo=linkedin)](https://linkedin.com/in/lucas-gaston-cabral)
[![Email](https://img.shields.io/badge/Email-Contacto-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:Lucassimple@hotmail.com)
[![Portfolio](https://img.shields.io/badge/Portfolio-Visitar-2F81F7?style=for-the-badge&logo=google-chrome&logoColor=white)](https://bit.ly/47unnek)
[![GitHub](https://img.shields.io/badge/GitHub-Seguir-181717?style=for-the-badge&logo=github)](https://github.com/Lucascabral95)

</div>

---

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,12,20&height=100&section=footer" alt="Footer"/>
  
  ### 💭 "La simplicidad es la máxima sofisticación" - Leonardo da Vinci
  
</div>
