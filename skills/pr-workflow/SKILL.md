---
name: pr-workflow
description: Plan commits and PRs, address CI failures, or assess merge readiness within the requested delivery scope.
---

# PR 작업

사용자가 요청한 전달 단계까지 진행합니다. PR 준비·병합 가능 상태 확인은 병합·배포 승인이 아닙니다.

- 기본은 작업당 저장소별 PR 하나와 목적별 논리 커밋입니다. 사용자 지시와 저장소 정책을 우선합니다.
- 검증·전달 경계가 필요하면 [전달 계약](references/delivery-contract.md)을 읽습니다. 변경 영향과 저장소 필수 검사에 맞게 검증하고 유효한 결과는 재사용합니다.
- 커밋 분할·여러 저장소 의존성은 [묶음 기준](references/grouping-rules.md), PR 작성·리뷰·CI·병합은 [GitHub 절차](references/github-review-loop.md)를 참조합니다. 상태 질의는 필요한 상태만 조회합니다.
- 작업 환경의 선택·격리·정리가 필요하면 [worktree 생명주기](references/worktree-lifecycle.md)를 참조합니다.
- 반복하거나 수렴하지 않는 리뷰에는 `review-radius`, 요청된 독립 QA나 위험상 필요한 검증에는 `traceknot`을 사용할 수 있습니다. 선택 도구 부재 자체를 작업 중단 사유로 만들지 않습니다.
- 리뷰 의견의 타당성을 코드·동작으로 확인하고, 승인된 범위에서 수정·검증·답글·해결 처리를 완료합니다. 결과는 현재 변경과 검증 대상, 남은 지적사항을 근거로 보고합니다.
- 새 PR 생성이 성공한 직후에만 [생성 후 처리](references/post-pr-create.md)를 읽고 수행합니다. PR 준비·상태 조회·기존 PR 리뷰·갱신만 할 때는 읽지 않습니다.
