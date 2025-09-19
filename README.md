# FightIQ

## Overview
FightIQ is a distributed, modular fight analytics platform that ingests fight clips (or live streams), extracts pose and event features, classifies actions/techniques, and produces highlight reels and coachable insights.

## Elevator Pitch
Imagine a coach or athlete uploading fight videos to a system that automatically analyzes the footage, identifies techniques, tracks actions per round, and produces visual insights and highlight reels. FightIQ combines real-time video processing, distributed systems, and ML action classification to deliver an end-to-end fight analytics platform.

## Why This Project
- Showcases distributed systems expertise: stream processing, microservices, scaling.  
- Highlights ML and computer vision skills: pose estimation, temporal action recognition, embeddings.  
- Creates a unique, demo-friendly product: visually appealing, personally aligned with UFC/BJJ interests.  
- Monorepo-ready for clean management of multiple services, apps, and libraries.  

## Key Components
**Monorepo Layout:**
- `/apps/dashboard` — Next.js dashboard for video replay, timeline, and analytics  
- `/services/ingest` — Video upload and orchestrator  
- `/services/frame-extractor` — Extract frames from uploaded videos  
- `/services/pose` — Pose estimation microservice (MediaPipe/OpenPose wrapper)  
- `/services/action-classifier` — Temporal ML model to classify actions  
- `/services/indexer` — Stores embeddings, keypoints, and events  
- `/libs/annotations` — Annotation UI & labeling pipeline  
- `/ml` — Model training notebooks, pipelines  
- `/infra` — Terraform/Kubernetes manifests  
- `/ops` — CI/CD, monitoring, metrics  
- `/docs` — Architecture, API, and usage docs  

## First Steps
1. Initialize the monorepo with the above structure.  
2. Set up basic CI/CD and dev pipelines.  
3. Implement Sprint 0: monorepo scaffold + dashboard skeleton.  
4. Begin planning seed data collection for meaningful action detection models.  

## Seed Data Plan
We need a large set of labeled fight clips to train the action classifier.  

**Steps include:**  
- **Source Data:**  
  - Publicly available MMA/UFC fight clips (YouTube API, public databases).  
  - BJJ competition videos (open source or creative commons licensed).  
  - Amateur annotated fight datasets if available.  

- **Preprocessing:**  
  - Clip segmentation (split full fights into 10–30s segments).  
  - Standardize video resolution and frame rate.  
  - Label each clip with round, action type (strike, takedown, guard-pass, submission attempt, etc.).  

- **Annotation:**  
  - Use a lightweight annotation tool in `/libs/annotations` to label frames or segments.  
  - Export labels to JSON/CSV for ML training.  

- **Storage:**  
  - Object store (S3/MinIO) for raw clips and frames.  
  - Database (Postgres/Timescale) for metadata and labels.  

- **Initial Dataset Size:**  
  - Aim for 500–1000 clips initially to have a meaningful MVP for action classification.  

## Next Steps
- Confirm monorepo initialization.  
- Start building seed dataset pipeline.  
- Decide on initial classes for action classification (strike, takedown, guard-pass, submission attempt, etc.).  
