# Checkmite

![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-6-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-Express-339933?style=for-the-badge&logo=node.js&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-Model_API-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)

> AI 이미지/영상 분석 기반 천적응애 사육 품질 관리 웹 애플리케이션

Checkmite는 사육박스별 이미지와 영상을 분석해 천적응애/먹이응애 탐지, 밀도 측정, 활력도 분석, 증식률 추적을 수행하는 로컬 실행형 연구 대시보드입니다. 연구자가 사육 상태를 정량화하고 시간 흐름에 따른 변화를 관리할 수 있도록 돕습니다.

## 프로젝트 목표

- **수작업 계수 부담 감소**: 현미경 기반 수동 계수 과정을 이미지/영상 분석으로 보조합니다.
- **사육 품질 데이터화**: 개체 수, 밀도, 활력도, 증식률을 사육박스별 이력으로 저장합니다.
- **로컬 우선 실행**: 현장 PC 또는 내부망 환경에서 프론트엔드, 백엔드, 모델 API를 실행할 수 있도록 구성합니다.
- **운영 중심 대시보드**: 모델 데모가 아니라 사육박스 등록, 분석, 저장, 비교까지 이어지는 업무 흐름을 제공합니다.

## 대상 사용자

- 천적응애 대량 사육 품질을 관리하는 농업 연구 인력
- 이미지/영상 기반 샘플 분석 결과를 사육박스별로 기록해야 하는 실험실 또는 배양실 운영자
- 인터넷 연결이 제한적인 환경에서 로컬 분석 도구가 필요한 현장 사용자

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

## 빠른 시작

상세 설치와 서버 설정은 Wiki를 기준으로 확인합니다.

```bash
npm install
npm run api:install
cp .env.example .env
npm run backend:migrate
```

서비스 실행 후 상태 확인:

```bash
curl http://127.0.0.1:80/
curl http://127.0.0.1:3000/api/health
curl http://127.0.0.1:8000/health
```

## Repo 구성

이 repo에는 애플리케이션 실행에 필요한 소스 코드와 최소 설정 파일만 포함합니다.

| 경로 | 설명 |
| --- | --- |
| `src/` | 프론트엔드 소스 |
| `backend/` | Express 백엔드 소스 |
| `api/` | Python 모델 API 소스 |
| `backend/db/schema.sql` | PostgreSQL schema |
| `.env.example` | 환경변수 예시 |

상세 설치 방법, 서버 설정, 기능 설명, API/DB 문서, 분석 문서는 GitHub Wiki에서 관리합니다.

## 문서

| 문서 | 내용 |
| --- | --- |
| [GitHub Wiki](https://github.com/checkmite/checkmiteV1/wiki) | 전체 문서 목차 |
| [설치 방법](https://github.com/checkmite/checkmiteV1/wiki/설치-방법) | Node.js, Python, PostgreSQL 설치 |
| [실행 방법](https://github.com/checkmite/checkmiteV1/wiki/실행-방법) | 프론트엔드, 백엔드, 모델 API 실행 |
| [환경변수 설정](https://github.com/checkmite/checkmiteV1/wiki/환경변수-설정) | `.env`와 `CHECKMITE_*` 설정 |
| [모델 파일 준비](https://github.com/checkmite/checkmiteV1/wiki/모델-파일-준비) | 모델 가중치 배치 방법 |
| [주요 기능](https://github.com/checkmite/checkmiteV1/wiki/주요-기능) | 화면별 기능 설명 |
| [API 문서](https://github.com/checkmite/checkmiteV1/wiki/API-문서) | 백엔드 및 모델 API 요약 |
| [DB 구조](https://github.com/checkmite/checkmiteV1/wiki/DB-구조) | 주요 테이블과 migration |

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
