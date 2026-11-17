# Esper Skills

Esper가 작성하거나 개인 작업 방식에 맞게 수정한 Agent Skills 모음입니다. 각 스킬은 `skills/<스킬명>/SKILL.md` 구조로 관리합니다.

## 포함된 스킬

| 스킬 | 용도 | 원본 출처 | MIT 저작권 표시 |
| --- | --- | --- | --- |
| [pr-workflow](skills/pr-workflow/) | 요청 범위에 맞춘 커밋·PR·리뷰·CI·병합 준비 | [Esper80/skills — pr-workflow](https://github.com/Esper80/skills/tree/main/skills/pr-workflow) | Copyright (c) 2026 Esper |
| [review-radius](skills/review-radius/) | 반복 리뷰의 근본 원인과 관련 경로 조사·수정·검증 | [Jin-Doh/review-radius](https://github.com/Jin-Doh/review-radius) | Copyright (c) 2026 KyungHo Kim |
| [traceknot](skills/traceknot/) | 요구사항·실행 증거에 따른 QA와 잔여 위험 평가 | [Jin-Doh/traceknot](https://github.com/Jin-Doh/traceknot) | Copyright (c) 2026 Traceknot contributors |

`review-radius`와 `traceknot`은 원본 그대로의 배포본이 아닌 로컬 수정본입니다. 일반 작업의 절차를 간소화하고 기존 결과 재사용과 승인 범위를 명확히 했으며, 엄격 모드의 실행 파일·schema·증거 및 판정 규칙은 유지했습니다. 각 폴더의 `LICENSE`와 `ATTRIBUTION.md`를 함께 보관해 주세요.

## 다른 PC에 설치

Node.js 22.20.0 이상과 `npx`가 필요합니다. GitHub에서 저장소를 읽을 수 있어야 합니다. 아래 명령은 Windows PowerShell, macOS 터미널 또는 Linux/WSL 터미널에서 실행합니다.

먼저 설치 가능한 스킬을 확인합니다.

```sh
npx skills add Esper80/skills --list
```

Codex에서 모든 프로젝트에 사용할 세 스킬을 설치합니다.

```sh
npx skills add Esper80/skills --skill pr-workflow review-radius traceknot --agent codex --global
```

한 스킬만 설치할 수도 있습니다.

```sh
npx skills add Esper80/skills --skill pr-workflow --agent codex --global
```

현재 프로젝트에만 설치하려면 `--global`을 생략합니다. 심볼릭 링크를 사용할 수 없는 환경에서는 명령 끝에 `--copy`를 추가합니다. 이미 같은 이름의 스킬이 있으면 기존 수정 내용을 먼저 확인하고 보존해 주세요. Windows와 WSL은 서로 다른 설치 환경이므로 사용할 환경의 터미널에서 설치합니다.

설치 후에는 Codex의 다음 대화 차례에서 `$pr-workflow`, `$review-radius`, `$traceknot`으로 요청할 수 있습니다. 도구별 기본 설치 경로는 [Skills CLI 문서](https://github.com/vercel-labs/skills/blob/main/docs/commands.md#skills-add)를 따릅니다. 이 저장소의 설치 검증에는 Skills CLI 1.9.0을 사용합니다. 같은 버전으로 설치하려면 위 명령의 `npx skills`를 `npx skills@1.9.0`으로 바꿉니다.

## 실행 환경과 사용 범위

- 일반 지침·문서 기반 사용과 엄격 모드의 실행 도구는 구분합니다. 필요한 도구는 실제로 선택한 작업에 맞게 준비합니다.
- `pr-workflow`는 Git·GitHub 접근과 사용 중인 에이전트의 도구를 활용합니다. Codex 앱 전용 PR 생성 후처리 도구가 없으면 수행되지 않은 후처리 상태를 명시합니다.
- `review-radius`의 엄격 모드 제어 스크립트는 Python 3과 Unix 계열의 `fcntl`을 사용합니다. Windows에서는 해당 스크립트를 WSL에서 실행합니다.
- `traceknot`의 번들 CLI는 Bun 1.3.14 이상과 macOS 또는 `libc.so.6`을 제공하는 glibc 기반 Linux 환경이 필요합니다. 기본 Windows와 musl 기반 Linux는 번들 CLI의 로컬 저장소·명령 수집 기능을 지원하지 않으므로 Windows에서는 WSL을 사용합니다.
- 프로젝트의 실제 필수 검사와 현재 사용자의 승인 범위를 우선합니다. 이 개인 맞춤 지침에 기록된 상시 승인을 다른 사용자에게 자동으로 적용하지 않습니다.

## 업데이트

이 수정본의 설치 출처는 `Esper80/skills`입니다. 현재 설치한 도구와 스킬의 로컬 변경을 확인한 뒤 Skills CLI로 필요한 스킬을 업데이트합니다.

```sh
npx skills update pr-workflow review-radius traceknot --global
```

`traceknot/bin/traceknot-skills-update`는 원본 `Jin-Doh/traceknot`의 릴리스·서명·설치 출처를 검증하는 도구입니다. 이 수정본의 업데이트 수단으로 실행하지 않습니다. 원본 업데이트가 필요하면 변경 내용을 검토해 이 저장소에 반영한 뒤 다시 설치합니다. 자동 업데이트 예약은 구성하지 않습니다.

## 라이선스와 출처

각 스킬의 라이선스 파일이 해당 스킬에 적용됩니다. 원본 두 스킬의 저작권자를 Esper로 변경하지 않습니다.

- [pr-workflow LICENSE](skills/pr-workflow/LICENSE) · [출처](skills/pr-workflow/ATTRIBUTION.md)
- [review-radius LICENSE](skills/review-radius/LICENSE) · [출처](skills/review-radius/ATTRIBUTION.md)
- [traceknot LICENSE](skills/traceknot/LICENSE) · [출처](skills/traceknot/ATTRIBUTION.md)

형식과 설치 도구에 대한 참고 자료: [Agent Skills 표준](https://agentskills.io/specification), [Skills CLI](https://github.com/vercel-labs/skills).
