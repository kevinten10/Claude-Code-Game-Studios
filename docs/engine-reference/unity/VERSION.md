# Unity Engine — Version Reference

| Field | Value |
|-------|-------|
| **Engine Version** | Unity 2021.3.11f1 (LTS) |
| **Project Pinned** | 2026-03-30 |
| **Last Docs Verified** | 2026-03-30 |
| **LLM Knowledge Cutoff** | May 2025 |
| **Risk Level** | LOW — version is within LLM training data |

## Note

This engine version (2021.3 LTS) is well within the LLM's training data.
No knowledge gap concerns. Engine reference docs are minimal.

## Key Packages

| Package | Version | Purpose |
|---------|---------|---------|
| URP | 17.0.3 | Rendering pipeline |
| XR Interaction Toolkit | 3.0.7 | VR interactions |
| Netcode for GameObjects | 2.1.1 | Multiplayer networking |
| Input System | 1.11.2 | Input handling |
| Addressables | 1.22.6 | Asset management |
| ML Agents | 3.0.0 | AI behavior |
| Barracuda | 3.0.0 | Neural network inference |
| TextMeshPro | 3.0.7 | Text rendering |

## Target Platform

- **Primary**: Android (PICO VR headsets)
- **Development**: Windows (Editor)

## Performance Targets

- **Frame Rate**: 90 FPS (PICO 4 requirement)
- **Latency**: <20ms motion-to-photon
- **Draw Calls**: <100 per frame
- **Memory**: <4GB total budget

## Verified Sources

- Official docs: https://docs.unity3d.com/2021.3/Documentation/Manual/
- C# API reference: https://docs.unity3d.com/2021.3/Documentation/ScriptReference/
- Release notes: https://unity.com/releases/editor/whats-new/2021.3.11
