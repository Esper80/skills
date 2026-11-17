# Traceability and coverage

일반 QA에서는 [기본 흐름](../SKILL.md)에 따라 현재 변경에 필요한 기술·관찰 기준을 사용합니다. 아래 전면 trigger scan·정형 ID·전체 profile·승인 산출물·인증된 증거 요구는 선택한 엄격 모드 또는 프로젝트가 요구하는 경우에 적용하며, 해당 모드의 기존 검증·판정 규칙은 유지합니다.

Maintain bidirectional links:

```text
basis ↔ risk ↔ condition ↔ obligation ↔ evidence ↔ defect
```

## Required checks

- every material basis ID has at least one condition;
- every R2/R3 risk has at least one mandatory obligation;
- every mandatory condition has exactly one terminal obligation result;
- every passing obligation has evidence bound to the target snapshot;
- every failed observation is linked to a defect or documented non-defect disposition;
- every accepted defect or residual risk has an unexpired approval;
- no evidence is reused across incompatible snapshots or conditions.

## Coverage report

Report counts and uncovered IDs for:

- basis coverage;
- risk coverage;
- condition execution coverage;
- mandatory obligation completion;
- supported platform/profile coverage when applicable;
- regression scope;
- optional code or branch coverage when the repository uses it.

A percentage without the uncovered identifiers is insufficient. Code coverage never substitutes for basis, risk, or condition coverage.
