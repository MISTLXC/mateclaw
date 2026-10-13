# Changelog

## 3.0.0-SNAPSHOT — In development

3.0.0-SNAPSHOT upgrades to Java 21, Spring Boot 4 and Spring AI 2. AgentScope 2 drives ReAct and plan-step execution loops; MateClaw retains approvals, permissions, Goals, SSE and persistence. This is a development snapshot.

- MyBatis Plus 3.5.17 with the Boot 4 starter; MCP SDK 0.18.3.
- Native DashScope chat/embedding adapters; native speech SDK retained.
- Owned HTTP cancellation, guarded tool batches and durable Goal checkpoints prevent blind side-effect replay.
- Existing frontend interaction contracts and conversation history remain supported.

[English details](mateclaw-server/src/main/resources/docs/en/changelog.md) · [中文说明](mateclaw-server/src/main/resources/docs/zh/changelog.md)

## Cumulative changes since 2.3.0

3.0.0-SNAPSHOT includes the former 2.4.0 development cycle; 2.4.0 was not published as a separate stable release. The groups below cover capabilities added before the architecture migration as well.

### Workspaces and conversations

- Optional member file isolation resolves personal files by member identity with shared-file fallback; existing workspace roles and default sharing still apply (#644).
- Persistent channel conversations expire stale query context. Uploaded images resolve from conversation storage; directory uploads retain directory metadata and validate containment.
- Employee drafts accept JSON following reasoning blocks, and explicit tool opt-out is respected even for general capabilities (#648, #655).

### Structured decisions, Goals, plans and teams

- A bounded typed Choice / Boolean / Score decision pipeline adds durable audit, OFF / SHADOW / ACTIVE modes and scenario overrides. SHADOW is the default; suggestions cannot bypass domain constraints.
- Goal continuation, plan employee routing and team worker-result judgment share the decision foundation. Domain transactions commit outcomes and state; delayed decisions validate identity and fences.
- Richer routing context, worker contracts, delegated-step result checks and bounded Goal recovery retain existing completion gates and record applied follow-up suppression.

### Models and DeepSeek Harness

- DSH moves to the SDK runtime with pinned versions and controlled upgrades. Failed health checks invalidate cached health and broken settings remain editable (#650).
- Model probes validate completed responses rather than accepting connection success or empty output (#658).

### Read-aloud, chat and tool presentation

- Edge and DashScope read-aloud are restored, with provider voice lists, selection and preview (#646).
- Structured MCP results get dedicated presentation below the final answer. Ordinary tool results no longer automatically become final-answer text (#651, #656, #661).

### Channels and database operations

- Application-owned Feishu WebSocket readiness and lifecycle release owned resources on shutdown and reconnect (#659).
- Unsupported webhook channels are rejected before configuration persistence (#654).
- Flyway validation failures block startup by default; history repair requires explicit opt-in, with backup and recovery guidance (#657).
- Commercial-edition overview and links are added; commercial modules are not included in the open-source edition.
