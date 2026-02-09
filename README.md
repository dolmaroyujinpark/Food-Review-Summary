<div align="center">

# Food Review Summarizer

**KoT5 Fine-tuning 기반 음식점 리뷰 자동 요약 시스템**

카카오맵 리뷰 크롤링부터 데이터 전처리, 모델 파인튜닝, 웹 배포까지의 End-to-End 파이프라인

[![Demo](https://img.shields.io/badge/Demo-Live-brightgreen?style=for-the-badge&logo=vercel)](https://review-summary-rho.vercel.app/)
[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)](https://pytorch.org)
[![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black)](https://huggingface.co)
[![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)](https://flask.palletsprojects.com)

</div>

---

## Demo

> **https://review-summary-rho.vercel.app/**

음식점 리뷰를 입력하면, Fine-tuned KoT5 모델이 핵심 내용을 자동으로 요약합니다.

---

## Overview

이 프로젝트는 **카카오맵 음식점 리뷰**를 수집하고, 이를 요약하는 NLP 모델을 학습 및 배포하는 전체 파이프라인을 포함합니다.

| 단계 | 설명 | 위치 |
|------|------|------|
| **데이터 수집** | Selenium 기반 카카오맵 리뷰 크롤링 | `datasetMaker/` |
| **데이터 전처리** | 이모지 제거, 초성 필터링, 리뷰 병합 | `datasetMaker/` |
| **모델 학습 (Project 1)** | KoT5 Fine-tuning 기반 요약 모델 | `project 1/` |
| **모델 학습 (Project 2)** | Sparse Transformer 직접 구현 (참고용) | `project 2/` |
| **웹 서비스** | Flask 기반 요약 API + Web UI | `app.py`, `static/` |

---

## Tech Stack

| Category | Technology |
|----------|------------|
| Language | Python |
| Deep Learning | PyTorch, HuggingFace Transformers |
| Model | KoT5 (Fine-tuned), Sparse Transformer |
| Data Collection | Selenium, BeautifulSoup |
| Backend | Flask |
| Frontend | HTML, CSS, JavaScript |
| Deployment | Vercel |

---

## Project Structure

```
Food-Review-Summary/
├── datasetMaker/                  # 데이터 수집 및 전처리
│   ├── 01_advancedScraper.py      #   카카오맵 리뷰 크롤러
│   ├── 02_review30ver.py          #   리뷰 병합 및 요약 데이터셋 생성
│   └── 03_emoji.py                #   이모지/초성 제거 전처리
│
├── project 1/                     # KoT5 Fine-tuning (최종 사용 모델)
│   ├── data/                      #   학습/테스트 데이터셋
│   ├── models/                    #   학습된 모델 저장
│   └── src1/
│       ├── dataset.py             #   데이터셋 로드 및 처리
│       ├── preprocess.py          #   데이터 전처리
│       ├── train.py               #   모델 학습
│       ├── evaluate1.py           #   모델 평가 (ROUGE 등)
│       ├── evaluate2.py           #   추가 평가 스크립트
│       └── utils.py               #   유틸리티 함수
│
├── project 2/                     # Sparse Transformer (참고용)
│   ├── data/                      #   데이터 및 토크나이저
│   ├── src2/
│   │   ├── components/            #   Transformer 구성 요소
│   │   │   ├── feed_forward.py
│   │   │   ├── multi_head_attention.py
│   │   │   ├── positional_encoding.py
│   │   │   └── transformer_block.py
│   │   ├── transformer.py         #   Sparse Transformer 모델
│   │   ├── dataset2.py            #   데이터셋 처리
│   │   ├── tokenizer.py           #   토크나이저
│   │   ├── train.py               #   모델 학습
│   │   └── evaluate.py            #   모델 평가
│   ├── main.py                    #   실행 진입점
│   ├── generate.py                #   요약 생성
│   └── generate_input_ver.py      #   입력 기반 요약 생성
│
├── static/
│   └── index.html                 # 웹 UI
├── app.py                         # Flask 웹 서버
└── README.md
```

---

## Getting Started

### 1. 환경 설정

```bash
git clone https://github.com/dolmaroyujinpark/Food-Review-Summary.git
cd Food-Review-Summary
pip install -r requirements.txt
```

### 2. 모델 학습 (Project 1 - KoT5)

```bash
# 학습
python "project 1/src1/train.py"

# 평가
python "project 1/src1/evaluate1.py"
```

### 3. 웹 서버 실행

```bash
python app.py
# http://127.0.0.1:5000 에서 확인
```

### 4. (참고) Sparse Transformer 실행

```bash
python "project 2/main.py"
```

---

## Pipeline

```
카카오맵 리뷰 크롤링 (Selenium)
        │
        v
데이터 전처리 (이모지/초성 제거, 리뷰 병합)
        │
        v
학습 데이터셋 생성 (JSON)
        │
        v
KoT5 모델 Fine-tuning
        │
        v
Flask 웹 서비스 배포
```

---

## Developer

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/dolmaroyujinpark">
        <img src="https://github.com/dolmaroyujinpark.png" width="120px;" alt="dolmaroyujinpark"/><br />
        <sub><b>dolmaroyujinpark</b></sub>
      </a>
    </td>
  </tr>
</table>

---

<div align="center">

**If you found this project helpful, please give it a star!**

</div>
