# 🛡️ DefenseOps AI

[![Next.js](https://img.shields.io/badge/Next.js-15-black?style=flat\&logo=nextdotjs)](https://nextjs.org/)
[![NestJS](https://img.shields.io/badge/NestJS-10-red?style=flat\&logo=nestjs)](https://nestjs.com/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?style=flat\&logo=typescript)](https://www.typescriptlang.org/)
[![Turborepo](https://img.shields.io/badge/Turborepo-Monorepo-lightgrey?style=flat\&logo=vercel)](https://turbo.build/)
[![AI Powered](https://img.shields.io/badge/AI-Powered-red?style=flat\&logo=openai)](https://openai.com/)
[![Security](https://img.shields.io/badge/Security-Military%20Grade-darkgreen)]()

**DefenseOps AI** est une plateforme SaaS / PWA pour la défense, pensée pour fonctionner en mode **offline-first**, intégrant des modules IA et des connecteurs sécurisés. Elle vise à unifier la gestion du matériel (MRO), des missions, des ressources humaines et de la logistique, avec une traçabilité complète et des standards de sécurité souverains.

---

## 🚀 Vision

Créer un **SaaS innovant pour les armées** :

* Centralisation des ressources et opérations.
* Automatisation via IA (maintenance prédictive, résumés, optimisations).
* Fonctionnement robuste en conditions dégradées.
* Extensibilité par connecteurs et plugins sécurisés.

---

## ✨ Fonctionnalités (MVP)

* 📦 **Inventaire & MRO** : équipements, pièces, certificats, ordres, historiques.
* 🎯 **Missions (lite)** : création, affectations, ordres & rapports auto.
* 🧑‍✈️ **Personnel & habilitations** : profils, compétences, expirations.
* 📊 **Rapports & audit** : exports, journaux immuables, indicateurs clés.
* 🔒 **Sécurité avancée** : RBAC/ABAC/MAC, chiffrement bout‑à‑bout.

**Extensions prévues (v1+)** : IA prédictive, analyse capteurs/drones, carto tactique, e‑learning, RAG doctrine, plugins connecteurs (ERP, GMAO, IoT).

---

## 🧱 Stack technique

* **Frontend** : Next.js 15 (App Router), React, TailwindCSS, shadcn/ui, Zustand.
* **Backend** : NestJS, PostgreSQL + Timescale, Prisma, Redis, OpenSearch.
* **Infra** : Kubernetes (OpenShift/AKS Gov/K3s), GitOps (ArgoCD), CI/CD GitHub Actions.
* **Bus** : NATS JetStream (edge) / Kafka (hauts débits).
* **IA/MLOps** : MLflow, BentoML, ONNX Runtime, RAG (pgvector/OpenSearch k‑NN).
* **Sécurité** : OIDC, MFA/FIDO2, OpenFGA/OPA, Cosign, SBOM, SLSA.
* **Observabilité** : OpenTelemetry, Prometheus, Grafana, Pact (tests de contrats).

---

## ⚡ Démarrage rapide

```bash
# 1) Cloner le repo
git clone https://github.com/<ORG_OR_USER>/defenseops-ai.git
cd defenseops-ai

# 2) Installer les dépendances
npm install

# 3) Lancer la base de données
docker compose -f infra/docker/compose.dev.yml up -d

# 4) Générer le schéma Prisma
npm run db:push --workspace=@defenseops/api

# 5) Démarrer l’environnement de dev
npm run dev
```

---

## 🗺️ Roadmap

### Phase 0 – Préparation (2 semaines)

* ✅ Cadrage stratégique & architecture.
* 🔧 Setup repo monorepo (Turborepo, workspaces).
* 🔒 Définition baseline sécurité (RBAC, chiffrement, CI/CD sécurisé).

### Phase 1 – MVP fondations (8 semaines)

* **S1-S2** : Ateliers besoins, design UX (Inventaire, Mission).
* **S3-S4** : MVP Inventaire/MRO (CRUD + ordres + certificats + audit).
* **S5-S6** : Module Missions (lite), génération auto d’ordres & résumés IA basiques.
* **S7-S8** : AuthN/Z (OIDC, RBAC/ABAC), sync offline chiffrée, journaux append-only.

### Phase 2 – IA & connecteurs (10 semaines)

* **IA prédictive** : modèles sur séries temporelles (pannes, anomalies).
* **Connecteurs v1** : IAM (SCIM), IoT (MQTT/OPC-UA), ERP (SAP/Maximo), SIG.
* **Carto tactique** : intégration cartes SIG, suivi missions.
* **MLOps pipeline** : MLflow, registry modèles, tests robustesse.

### Phase 3 – Extension métier (12 semaines)

* **E-learning & training** : modules de formation avec suivi IA.
* **Optimisation affectations** (solveur contraintes : compétences, habilitations, fatigue).
* **Intégration drones/UAV** (imagerie, MAVLink, détection anomalies).
* **Durcissement sécurité** : pentests, bug bounty restreint, SLSA supply chain.

### Phase 4 – Scalabilité & industrialisation

* **Multi‑tenancy avancé** : isolation par cluster/namespace, clés KMS par tenant.
* **Observabilité complète** : 95% couverture traces/logs/metrics corrélées.
* **Conformité** : ISO 27001, ANSSI/SecNumCloud (FR), ITSG‑33 (CA), STANAG OTAN.
* **Préparation déploiements SaaS dédiés et On‑prem/air‑gapped.**

---

## 📜 Licence

**Propriétaire – Usage Défense uniquement.**

---

## 🤝 Contribution

PRs bienvenues sur des modules non sensibles (UI, DX, perf). Merci d’ouvrir des issues pour les propositions.

---

## ✅ KPI cibles

* Disponibilité SaaS dédié : 99.9%.
* p95 API < 200 ms intra‑théâtre.
* MTTR incidents P1 < 1h.
* Couverture traces OTel ≥ 95%.
* Taux d’échec sync offline < 0.1%.
