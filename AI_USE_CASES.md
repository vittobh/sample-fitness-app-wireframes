# AI Use Cases (2026) — Fitness Wellness Coach

## Agentic upgrade
Five-agent wellness crew (LangGraph):
1. **Ingestion** — Health Connect / Google Fit / Apple Health → FHIR Observation
2. **Threshold detector** — HbA1c, BP, HR, glucose deltas crossing ADA / JNC-8 limits
3. **RAG recommender** — Claude Sonnet over clinical guideline corpus (ADA, JNC-8, WHO public abstracts)
4. **Personaliser** — Gemini multimodal (form-check from webcam, body-pose feedback)
5. **Alerter** — push / SMS / EHR write-back via FHIR

## Stack (free/OSS)
- **LLMs:** Claude Sonnet 4.6 (recommendations), Gemini 2.x (multimodal vision), Ollama + Llama 3 (private on-device fallback for PHI)
- **ASR:** Whisper / Faster-Whisper (voice food logging)
- **RAG:** LlamaIndex + Qdrant (or pgvector); spaCy for entity extraction
- **MCP:** Health Connect MCP server, FHIR MCP server
- **Eval:** Promptfoo (alert precision golden set), Inspect
- **Observability:** Langfuse · Arize Phoenix
- **Coding agents:** Claude Code (Health Connect integration), Cursor, Aider

## Prompt pattern (system)
```
You are a clinical wellness coach. Rules:
- Cite source guideline (ADA, JNC-8, WHO) on every recommendation.
- Never make diagnosis claims — recommend "consult clinician" for any abnormal threshold.
- Quote the exact guideline clause when citing.
- If user data is missing, ask before recommending.
```

## Eval hook
```yaml
prompts: ["file://prompts/coach.txt"]
providers: ["anthropic:claude-sonnet-4-6"]
tests:
  - vars: { hba1c: 7.2 }
    assert:
      - type: contains
        value: "ADA"            # must cite ADA guideline
      - type: not-contains
        value: "diagnos"        # no diagnosis language
      - type: llm-rubric
        value: "Cites guideline with section; recommends clinician consult; specific numeric target"
```

## Limitations
Real wearable ingestion needs native app (web prototype is mocked). Voice uses Web Speech API; Whisper local needs server.
