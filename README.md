# Checkmite

Checkmite는 AI 이미지/영상 분석 기반 천적응애 사육 품질 관리 웹 애플리케이션입니다.

사육박스별 이미지와 영상을 분석해 천적응애/먹이응애 탐지, 밀도 측정, 활력도 분석, 증식률 추적을 수행하고 연구자가 사육 상태를 시간 흐름에 따라 관리할 수 있도록 돕습니다.

## 주요 기능

- 사육박스 등록, 수정, 휴지통 이동 및 복구
- 이미지 기반 천적응애/먹이응애 객체 탐지
- 영상 기반 밀도 분석
- 영상 기반 활력도 분석과 tracking overlay 영상 생성
- 사육박스별 측정 이력 저장
- 직전 측정 및 첫 측정 대비 증식률 분석

## 시스템 구성

```text
Frontend       React + Vite + TypeScript
Backend        Express + Node.js
Database       PostgreSQL
Model API      FastAPI + Ultralytics YOLO + OpenCV/ONNX Runtime
```

기본 로컬 실행 포트:

```text
Frontend       http://localhost:80
Backend API    http://localhost:3000/api
Model API      http://localhost:8000
PostgreSQL     localhost:5432
```

## Repo 구성

이 repo에는 애플리케이션 실행에 필요한 소스 코드와 최소 설정 파일만 포함합니다.

- `src/`: 프론트엔드 소스
- `backend/`: Express 백엔드 소스
- `api/`: Python 모델 API 소스
- `backend/db/schema.sql`: PostgreSQL schema
- `.env.example`: 환경변수 예시

상세 설치 방법, 서버 설정, 기능 설명, API/DB 문서, 분석 문서는 GitHub Wiki에서 관리합니다.

## 문서

- [GitHub Wiki](https://github.com/checkmite/checkmiteV1/wiki)
- [설치 방법](https://github.com/checkmite/checkmiteV1/wiki/설치-방법)
- [실행 방법](https://github.com/checkmite/checkmiteV1/wiki/실행-방법)
- [환경변수 설정](https://github.com/checkmite/checkmiteV1/wiki/환경변수-설정)
- [모델 파일 준비](https://github.com/checkmite/checkmiteV1/wiki/모델-파일-준비)
- [주요 기능](https://github.com/checkmite/checkmiteV1/wiki/주요-기능)

## Repo에 포함하지 않는 파일

다음 파일은 GitHub repo에 올리지 않습니다.

- `.env`와 서버별 비밀 환경변수
- 업로드 이미지/영상과 분석 산출물
- 원본 연구 문서와 추출 텍스트
- DB dump와 백업 파일
- 모델 가중치 파일
  - `model/best.pt`
  - `model/vitality/best1.onnx`
- 학습 노트북과 실험용 산출물

실제 모델 파일은 별도로 전달받아 Wiki의 모델 파일 준비 문서에 따라 배치해야 합니다.

## 상태 확인

서비스 실행 후:

```bash
curl http://127.0.0.1:80/
curl http://127.0.0.1:3000/api/health
curl http://127.0.0.1:8000/health
```
