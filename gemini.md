# Project Constitution (Gemini.md)

## Data Schemas

### 1. User Input
```json
{
  "requirement": "String - The feature or functional requirement from the user.",
  "context": "String (Optional) - Additional context or constraints."
}
```

### 2. Test Case Output (The Payload)
The LLM should generate test cases in this structured format (JSON):
```json
{
  "testCases": [
    {
      "id": "String - e.g., TC001",
      "title": "String - Concise title of the test case",
      "description": "String - Detailed description",
      "preConditions": "String - What must be true before testing",
      "steps": [
        "Step 1...",
        "Step 2..."
      ],
      "expectedResult": "String - What should happen"
    }
  ]
}
```

## Behavioral Rules
- **Strict Template Adherence:** The LLM MUST follow the defined test case template.
- **Deterministic Output:** Output should be valid JSON to be easily parsed by the UI.
- **Model:** Use `llama3.2` via Ollama.
- **Tone:** Professional, QA-focused.

## Project Vision (North Star)
Create a Local LLM Test Case Generator using Ollama (Llama 3.2). It will take user input via a Web UI, use a predefined internal template, and generate structured test cases.

## Integration & Stack
- **Frontend:** Vanilla HTML/CSS/JS (Served by Python).
- **Backend/Service:** Python custom HTTP server (Acts as Host + Proxy).
- **AI Engine:** Ollama running `gemma3:1b`.
- **Note:** Node.js was not found, so React/Vite was replaced with a lightweight Python stack.

## Architectural Invariants
- **Protocol:** B.L.A.S.T.
- **Architecture:** A.N.T. 3-Layer (SOPs -> Navigation -> Tools)
- **Data-First:** Schema must be defined before code.
- **Self-Healing:** Analyze -> Patch -> Test -> Update Architecture.
- **Structure:**
  - `architecture/`: SOPs
  - `tools/`: Deterministic scripts
  - `.tmp/`: Intermediate files
