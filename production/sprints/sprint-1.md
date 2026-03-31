# Sprint 1 — 2026-03-30 to 2026-04-13

## Sprint Goal

用 GLM 替换 Mock AI 服务，让 AI 导游和 NPC 能真实对话。

## Capacity

- Total days: 14 (2 weeks)
- Buffer (20%): 3 days reserved for unplanned work
- Available: 11 days

## Tasks

### Must Have (Critical Path)

| ID | Task | Agent/Owner | Est. Days | Dependencies | Acceptance Criteria |
|----|------|-------------|-----------|-------------|-------------------|
| S1-01 | 创建 `GLMConfig` ScriptableObject | gameplay-programmer | 0.5 | — | 包含 apiKey, model, endpoint, temperature, maxTokens, fallback 开关 |
| S1-02 | 实现 `GLMService.cs`（实现 `IGPTService`） | ai-programmer | 2 | S1-01 | SendChatAsync + SendStreamChatAsync + GenerateContentAsync 通过测试 |
| S1-03 | 实现 SSE 流式解析 | ai-programmer | 1 | S1-02 | 逐 chunk 回调正确，`[DONE]` 后不再解析 |
| S1-04 | 实现三级 Fallback（GLM → Ollama → Mock） | ai-programmer | 1 | S1-02 | GLM 断开后 5s 内自动切换 Ollama |
| S1-05 | 修改 `AIServiceManager.InitializeLLMService()` | gameplay-programmer | 0.5 | S1-02 | Manager 启动后 `services[LLM]` 为 GLMService 实例 |
| S1-06 | AI Tour Guide 适配 GLM | ai-programmer | 1 | S1-05 | 导游对话使用 GLM 返回真实回复，多轮上下文连贯 |
| S1-07 | AI NPC System 适配 GLM | ai-programmer | 1 | S1-05 | NPC 对话流式输出，行为树正常触发 |

### Should Have

| ID | Task | Agent/Owner | Est. Days | Dependencies | Acceptance Criteria |
|----|------|-------------|-----------|-------------|-------------------|
| S1-08 | 速率限制 + 指数退避重试 | ai-programmer | 0.5 | S1-02 | 429 响应后退避重试，不超过 3 次 |
| S1-09 | 对话历史上下文窗口截断 | ai-programmer | 0.5 | S1-02 | 超 maxConversationLength 时截断旧消息，保留 system prompt |
| S1-10 | GLM 配置文档 + API Key 获取指南 | — | 0.5 | S1-01 | docs/GLM_SETUP.md 完成 |

### Nice to Have

| ID | Task | Agent/Owner | Est. Days | Dependencies | Acceptance Criteria |
|----|------|-------------|-----------|-------------|-------------------|
| S1-11 | GLM 健康检查 + 自动恢复 | ai-programmer | 0.5 | S1-04 | Degraded 状态定期探测，恢复后自动切回 GLM |
| S1-12 | Token 用量统计日志 | ai-programmer | 0.5 | S1-02 | 每次请求记录 input/output token 数 |

## Carryover from Previous Sprint

N/A — First sprint.

## Risks

| Risk | Probability | Impact | Mitigation |
|------|------------|--------|------------|
| GLM API 响应延迟超标 (>2s 首 token) | Medium | High | 先用免费 Flash 模型测试延迟基线 |
| 智谱 AI 平台注册/API Key 获取受阻 | Low | High | 备选：通过阿里云百炼调用 GLM |
| SSE 流式解析在 Unity WebRequest 中兼容性 | Medium | Medium | 参考现有 OpenAI SSE 解析逻辑，已验证可行 |

## Dependencies on External Factors

- 智谱 AI 开放平台账号 + API Key
- 网络环境可访问 `open.bigmodel.cn`

## Definition of Done for this Sprint

- [ ] All Must Have tasks (S1-01 ~ S1-07) completed
- [ ] AI 导游在 Editor Play Mode 下产生真实 GLM 回复
- [ ] NPC 流式对话正常工作
- [ ] Fallback 到 Ollama/Mock 验证通过
- [ ] 代码中无硬编码 API Key
- [ ] GDD Acceptance Criteria 全部通过
- [ ] design/gdd/glm-service-integration.md 状态更新为 Implemented
