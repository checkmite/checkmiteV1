# Checkmite

Checkmite is a local-first web application for managing predatory mite culture quality with AI-based image and video analysis.

The system helps researchers register culture boxes, analyze microscope or macro camera media, store analysis results, and review density, vitality, and growth trends over time.

## What It Does

- Manage culture boxes and sample history.
- Detect predatory mites and prey mites from still images.
- Estimate density from short sample videos.
- Analyze vitality with video tracking, movement metrics, and activity scores.
- Render tracking overlay videos for vitality review.
- Compare growth trends by culture box.
- Preserve deleted culture boxes in a trash/restore workflow.

## System Overview

```text
Frontend       React + Vite + TypeScript
Backend        Express + Node.js
Database       PostgreSQL
Model API      FastAPI + Ultralytics YOLO + OpenCV/ONNX Runtime
```

Default local runtime ports:

```text
Frontend       http://localhost:80
Backend API    http://localhost:3000/api
Model API      http://localhost:8000
PostgreSQL     localhost:5432
```

## Repository Contents

This repository contains the application source code, database schema, API documentation, and project analysis documents.

Included:

- `src/`: frontend application
- `backend/`: Express API server and PostgreSQL repositories
- `api/`: Python model runtime server
- `docs/`: backend/API architecture documents
- `프로젝트-분석문서/`: Korean project analysis documents
- `backend/db/schema.sql`: database schema and migration source
- `model/model-card.md`: model notes

Not included:

- `.env` or other private environment files
- uploaded image/video files
- original research documents and extracted document text
- database dumps
- model weight files such as `model/best.pt` and `model/vitality/best1.onnx`

Model files must be distributed separately and placed in the documented paths before running real inference.

## Documentation

Detailed setup and operation guides are maintained in the GitHub Wiki:

- Installation
- Environment variables
- Model file preparation
- Running the frontend, backend, and model API
- Feature guide
- API and database guide
- Deployment and operation notes

Additional repository documents:

- [Backend API specification](docs/backend-api-spec.md)
- [Backend/model server architecture](docs/backend-model-server-architecture.md)
- [Model API README](api/README.md)

## Quick Health Checks

After starting all services:

```bash
curl http://127.0.0.1:80/
curl http://127.0.0.1:3000/api/health
curl http://127.0.0.1:8000/health
```

## License and Data Notice

Do not commit private environment values, uploaded sample media, original institutional documents, database backups, or model weight files to this repository.
