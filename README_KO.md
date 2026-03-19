# Claude Code Skills

> Claude Code의 기능을 확장하는 커스텀 스킬 정의 문서 모음으로, 슬래시 커맨드를 통해 구조화된 AI 워크플로우를 제공합니다.

## 개요

이 저장소에는 재사용 가능한 **Claude Code 스킬**이 포함되어 있습니다. 각 스킬은 모듈화된 명령어 세트로, Claude Code의 역량을 전문화된 워크플로우로 확장합니다. 슬래시 커맨드(예: `/commit-push`, `/translation-specialist`)로 호출하며, 일반적인 개발 작업을 위한 구조화되고 반복 가능한 프로세스를 제공합니다.

## 스킬 목록

| 스킬 | 커맨드 | 설명 |
|------|--------|------|
| **Analyze** | `/analyze` | 4-Layer 프롬프트 분석(어휘, 통사, 담화, 화용)을 실행하고 최적의 체인/에이전트/스킬 추천 |
| **Claude Strategy** | `/claude-strategy` | 프로젝트에 최적화된 Claude Code 사용전략 문서 자동 생성 |
| **Commit Push** | `/commit-push` | Conventional Commits 형식으로 스테이징, 커밋, 푸시 자동화 |
| **Memory Save** | `/memory-save` | 세션 작업 내용을 `~/.claude/memory/`에 중복 방지 및 `YYMM_SEQ_keyword.md` 명명 규칙으로 저장 |
| **PR Review** | `/pr-review` | PR 또는 git diff를 리뷰하고 `.pr-reviews/` 폴더에 구조화된 리포트 생성 |
| **Project Review** | `/project-review` | 아키텍처, 구조, 유지보수성을 다루는 프로젝트 전체 리뷰 |
| **README Gen** | `/readme-gen` | 프로젝트 폴더를 분석하여 README.md(영어) 및 README_KO.md(한국어) 자동 생성 |
| **Translation Specialist** | `/translation-specialist` | 4-Layer 언어학적 분석 기반 맥락 인식 전문 번역, 6개 도메인 및 4가지 번역 전략 지원 |
| **Vibe Dev** | `/vibe-dev` | 문서 주도 AI 페어 프로그래밍 방법론 (조사, 정의, 개발, 보고의 4단계) |

## 프로젝트 구조

```
Skills/
├── analyze/
│   └── SKILL.md              # 4-Layer 프롬프트 분석 스킬
├── claude-strategy/
│   ├── SKILL.md               # 프로젝트 전략 생성기
│   └── references/
│       └── strategy-template.md   # 12섹션 전략 템플릿
├── commit-push/
│   └── SKILL.md               # Git 커밋 & 푸시 자동화
├── memory-save/
│   └── SKILL.md               # 세션 메모리 영속화
├── pr-review/
│   └── SKILL.md               # PR 리뷰 워크플로우
├── project-review/
│   └── SKILL.md               # 프로젝트 전체 감사 워크플로우
├── readme-gen/
│   └── SKILL.md               # README 자동 생성
├── translation-specialist/
│   ├── SKILL.md               # 전문 번역 엔진
│   ├── reference.md           # 분류 체계 및 키워드 사전
│   ├── examples.md            # 실전 번역 예시 4종
│   └── linguistic_analysis.py # 자동 언어학적 분석 도구
└── vibe-dev/
    ├── SKILL.md               # 문서 주도 개발 방법론
    ├── REVIEW.md              # 리뷰 가이드라인
    └── references/
        ├── checkpoint-protocol.md  # 중단 세션 복구 프로토콜
        ├── document-templates.md   # 프로젝트 문서 템플릿
        ├── error-recovery.md       # 오류 처리 및 복구 절차
        ├── phase1-investigate.md   # 1단계: 조사
        ├── phase2-define.md        # 2단계: 정의
        ├── phase3-develop.md       # 3단계: 개발
        ├── phase4-report.md        # 4단계: 보고
        ├── usage-examples.md       # 실전 사용 예시
        └── zero-guess-protocol.md  # 추측 배제 코딩 프로토콜
```

## 주요 특징

- **모듈화 설계**: 각 스킬은 독립적인 `SKILL.md` 정의 파일로 구성
- **슬래시 커맨드 연동**: 모든 스킬은 Claude Code의 `/command` 시스템으로 호출 가능
- **구조화된 워크플로우**: 명확한 입력, 출력, 품질 검사를 포함하는 단계별 프로세스 정의
- **참조 자료**: 복잡한 스킬은 `references/` 하위 디렉토리에 보조 문서 포함
- **다국어 지원**: 번역 스킬은 학술적 기반(ISO 17100, Nida의 기능적 등가 이론)으로 6개 도메인 지원
- **품질 보증**: 각 워크플로우에 내장된 리뷰 및 검증 단계

## 사용법

### Claude Code에서 사용

스킬을 Claude Code의 스킬 디렉토리에 배치하면 로드됩니다. 설치 후 슬래시 커맨드를 입력하여 스킬을 호출합니다:

```
/analyze "사용자 관리 REST API 구축"
/commit-push
/vibe-dev 날씨 대시보드 앱 만들기
/translation-specialist
```

### 스킬 정의 형식

각 스킬은 YAML 프론트매터가 포함된 `SKILL.md` 파일로 정의됩니다:

```yaml
---
name: skill-name
description: 스킬이 수행하는 작업
user-invocable: true
allowed-tools: [Bash, Read, Write]
---

# 스킬 명령이 마크다운으로 이어집니다...
```

## 라이선스

MIT

---

*[Claude Code](https://claude.ai/code)를 위해 AnsibleMage가 제작*
