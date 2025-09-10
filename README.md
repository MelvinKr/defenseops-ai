# 🛡️ DefenseOps AI

[![Next.js](https://img.shields.io/badge/Next.js-15-black?style=flat\&logo=nextdotjs)](https://nextjs.org/)
[![NestJS](https://img.shields.io/badge/NestJS-10-red?style=flat\&logo=nestjs)](https://nestjs.com/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?style=flat\&logo=typescript)](https://www.typescriptlang.org/)
[![Turborepo](https://img.shields.io/badge/Turborepo-Monorepo-lightgrey?style=flat\&logo=vercel)](https://turbo.build/)
[![AI Powered](https://img.shields.io/badge/AI-Powered-red?style=flat\&logo=openai)](https://openai.com/)
[![Security](https://img.shields.io/badge/Security-Military%20Grade-darkgreen)]()

**DefenseOps AI** est une plateforme SaaS / PWA pensée pour le **secteur militaire et défense**. Elle fonctionne en mode **offline-first**, inclut des modules IA et des connecteurs sécurisés, et vise à unifier la gestion **des matériels (MRO), des missions opérationnelles, des ressources humaines militaires et de la logistique tactique**, avec **traçabilité complète et standards de sécurité OTAN/ANSSI**.

---

## 🚀 Vision militaire

* Centraliser l’information opérationnelle : matériels, personnels, missions, doctrines.
* Automatiser la charge administrative par l’IA : ordres de mission, rapports post‑opération, planifications.
* Fonctionner en environnement contraint : connexions faibles, conditions dégradées, théâtres isolés.
* Intégrer des **connecteurs terrain** : SIG, capteurs IoT, UAV/drones, GMAO militaires, systèmes logistiques existants.

---

## ✨ Fonctionnalités (MVP)

* 📦 **Inventaire & MRO militaire** : véhicules, armements, drones, pièces détachées, certificats d’armement.
* 🎯 **Planification de mission (lite)** : création d’objectifs, affectations soldats/équipes, génération automatique d’ordres.
* 🧑‍✈️ **Personnel & habilitations** : profils soldats, compétences, formations, certificats médicaux et de tir.
* 📊 **Rapports & audit** : journaux immuables, exports sécurisés, indicateurs opérationnels (disponibilité, readiness).
* 🔒 **Sécurité** : RBAC/ABAC/MAC avec labels OTAN (Non classifié, Protégé, Confidentiel, Secret).

**Extensions prévues (v1+)** :

* 🔮 IA prédictive pour anticiper pannes véhicules/armements.
* 📡 Analyse des capteurs IoT et UAV (imagerie, anomalies).
* 🗺️ Cartographie tactique intégrée (SIG militaire).
* 🎓 E‑learning militaire (doctrine, entraînement, évaluation IA).
* 📑 RAG doctrinal pour consultation rapide de manuels et ordres OTAN.
* 🔌 Connecteurs sécurisés (SAP Défense, Maximo, systèmes SIG, IAM militaires).

---
## 🛣️ Avancement Roadmap (Septembre 2025 – Mise à jour)

## Phase 0 – Préparation & socle (S0-S3)

### S0–S1 : Cadrage stratégique & architecture

* [ ] Définir personas (officier, technicien MRO, soldat, SSI, analyste)
* [ ] Rédiger note d’architecture (principes, contraintes OTAN/ANSSI)
* [ ] Identifier modules MVP (Inventaire, Missions, Personnel)
* [ ] **AC** : document validé par stakeholders

### S1–S2 : Setup repo & CI/CD

* [ ] Initialiser monorepo (Turborepo, npm workspaces)
* [ ] Configurer TypeScript strict, ESLint, Prettier, Husky
* [ ] Pipeline CI GitHub Actions : build, test, lint
* [ ] Générer SBOM (Syft), signature artefacts (Cosign)
* [ ] **AC** : pipeline vert < 10 min

### S2–S3 : Baseline sécurité & infra dev

* [ ] Déployer Keycloak (OIDC) en dev
* [ ] Mettre en place Postgres 15 + Timescale extension
* [ ] Init MinIO (S3) pour fichiers
* [ ] NATS JetStream déployé (bus events dev)
* [ ] **AC** : dev env up en < 15 min via `docker compose`

---

## Phase 1 – MVP (8 semaines)

### S1–S2 : Inventaire & Maintenance (MRO)

* [ ] Modèle de données v1 (Prisma/Postgres)

  * [ ] Schémas initiaux : `Asset`, `Part`, `Certificate`, `MaintenanceOrder`, `Stock`, `Movement`, `Attachment`, `AuditLog`
  * [ ] Contraintes & index (FK, uniques, enums Prisma)
  * [ ] Seeds (10 assets, 40 parts, 5 certs/asset, 3 stocks)
  * [ ] **AC** : migrations ok, seeds ok, requêtes p95 < 50 ms
* [ ] API MRO (NestJS)

  * [ ] Endpoints CRUD (assets, parts, certificates, maintenance-orders, stocks)
  * [ ] Events NATS : `mro.maintenanceOrder.*`, `stock.movement.created`
  * [ ] Swagger + tests e2e ≥ 80%
* [ ] Front Inventaire (Next.js)

  * [ ] Pages liste/détail, scan QR, upload MinIO, export CSV
  * [ ] ag-Grid, SWR cache, SSR streaming
  * [ ] **AC** : Lighthouse > 90, fiche < 3 clics
* [ ] Piste d’audit immuable

  * [ ] Outbox + hash chain + ancrage Merkle
  * [ ] CLI `audit verify`
* [ ] Qualité & DX

  * [ ] ESLint/Prettier/TS strict, Husky hooks
  * [ ] CI : CodeQL, Syft, Cosign, preview env

### S3–S4 : Missions (lite)

* [ ] Modèle de données Missions (`Mission`, `Task`, `Assignment`, `RuleOfEngagement`, `Geofence`)
* [ ] API Missions (CRUD missions, tasks, assignments, rules, geofences)
* [ ] Events NATS : `mission.*`
* [ ] Génération PDF ordre de mission
* [ ] Front Missions (liste, détail, timeline, checklists)
* [ ] Résumé post-mission (IA v0, RAG minimal)

### S5–S6 : Personnel & habilitations

* [ ] Modèle de données Personnel (`Person`, `Clearance`, `Skill`, `Medical`, `Qualification`)
* [ ] API Personnel (CRUD, alertes expirations via Temporal)
* [ ] Events NATS : `person.skill.expiring`, `person.clearance.revoked`
* [ ] Front Personnel (liste, profil, matrice compétences, readiness)
* [ ] **AC** : 10 expirations proches détectées + alertes visibles

### S7–S8 : Sécurité & Offline

* [ ] AuthN/AuthZ (OIDC + MFA/FIDO2)
* [ ] RBAC, ABAC, MAC (labels OTAN)
* [ ] Tests unitaires sur scénarios d’accès (100% conformes)
* [ ] Offline-first : CRDT (Automerge/Y.js) + IndexedDB chiffré
* [ ] Sync journal chiffré + résolutions de conflits
* [ ] Journaux immuables & audit (hash chain + Merkle)
* [ ] **AC** : 5 scénarios offline simulés OK

---

## Phase 2 – IA & Connecteurs (10 semaines)

### S1–S3 : IA prédictive

* [ ] Ingestion séries (TimescaleDB hypertables)
* [ ] Features : fenêtres, dérivées, FFT
* [ ] Modèles anomalies (IsolationForest/Autoencoder), RUL (Prophet/TCN)
* [ ] Serving : BentoML + ONNX Runtime
* [ ] **AC** : latence < 50ms, rollback canary ok

### S4–S6 : Connecteurs v1

* [ ] SDK Node (auth, retry, DLQ, OTel)
* [ ] IAM SCIM/LDAP → sync Person/Unit
* [ ] IoT MQTT/OPC-UA ingestion temps réel
* [ ] SIG ArcGIS/QGIS import zones/rasters
* [ ] **AC** : 10k msg/min supporté

### S7–S10 : Cartographie & logistique

* [ ] Carto tactique : Maplibre/Deck.gl, couches missions/assets/geofences
* [ ] Tracking équipements (pos, ETA)
* [ ] Réappro : seuils, suggestions IA multi-dépôts
* [ ] **AC** : simulation rupture → -30% ruptures

---

## Phase 3 – Extensions opérationnelles (12 semaines)

### S1–S3 : E-learning militaire

* [ ] LMS intégré (cours, quiz, SCORM)
* [ ] IA adaptative (progression)
* [ ] RAG doctrinal (pgvector/OpenSearch)
* [ ] **AC** : +20% score cohorte test

### S4–S6 : Optimisation des ressources

* [ ] Solveur contraintes (OR-Tools/CP-SAT)
* [ ] Objectifs readiness↑, rotations↓
* [ ] What-if planning + comparaison scénarios

### S7–S9 : UAV & imagerie

* [ ] Intégration MAVLink, upload vidéo/logs
* [ ] Métadonnées vol (GPS, altitude…)
* [ ] Détection objets/anomalies (YOLOv8-ONNX/OpenVINO)
* [ ] **AC** : latence < 200ms/frame

### S10–S12 : Sécurité avancée

* [ ] Durcissement infra (CIS k8s, Kyverno)
* [ ] Supply chain : SLSA v3, SBOM Syft, Cosign
* [ ] Pentests + bug bounty restreint
* [ ] **AC** : 0 critique, High corrigés < 7j

---

## Phase 4 – Scalabilité & industrialisation (6+ mois)

### Multi-tenancy & déploiements

* [ ] Isolation cluster/namespace par tenant
* [ ] Clés KMS/HSM par tenant, schéma Postgres dédié
* [ ] Déploiement air-gapped (registry privé, Helm scellé)
* [ ] **AC** : chaos tests réseau OK

### Interopérabilité OTAN & conformité

* [ ] Mapping formats STANAG
* [ ] Propagation labels MAC
* [ ] ISO 27001, SecNumCloud, ITSG-33
* [ ] **AC** : audit interne passé

### Observabilité complète

* [ ] OTel traces/metrics/logs corrélés
* [ ] SLO/SLA : p95, budgets erreurs
* [ ] Drift IA détecté < 24h, rollback auto
* [ ] **AC** : couverture ≥ 95%, MTTR < 1h
      
---

## 🧱 Stack technique

* **Frontend** : Next.js 15 (App Router), React, TailwindCSS, shadcn/ui, Zustand, PWA offline-first.
* **Backend** : NestJS, PostgreSQL + Timescale (données + télémétrie capteurs), Prisma, Redis, OpenSearch.
* **Infra** : Kubernetes (AKS Gov, OpenShift, K3s edge/air‑gap), GitOps (ArgoCD), CI/CD GitHub Actions.
* **Bus** : NATS JetStream (edge theaters) ou Kafka (bases arrières).
* **IA/MLOps** : MLflow, BentoML, ONNX Runtime, OpenV

