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

## 🧱 Stack technique

* **Frontend** : Next.js 15 (App Router), React, TailwindCSS, shadcn/ui, Zustand, PWA offline-first.
* **Backend** : NestJS, PostgreSQL + Timescale (données + télémétrie capteurs), Prisma, Redis, OpenSearch.
* **Infra** : Kubernetes (AKS Gov, OpenShift, K3s edge/air‑gap), GitOps (ArgoCD), CI/CD GitHub Actions.
* **Bus** : NATS JetStream (edge theaters) ou Kafka (bases arrières).
* **IA/MLOps** : MLflow, BentoML, ONNX Runtime, OpenV
