# 🛡️ MCP-AGENTIC-CONTROL-LAB

**Enterprise RAG System built on Model Context Protocol (MCP) Agent → Tool → Context Architecture**

---

## 📖 Overview

**MCP-AGENTIC-CONTROL-LAB** is a production-grade enterprise RAG system that places authority, trust, and security directly inside **Model Context Protocol (MCP) Tool Boundaries**.

Instead of relying on UI-layer checks or prompt-engineering tricks, **MCP-Native Control** enforces access policy and audit logging inside tool contracts (`retrieve_policy_context`, `update_policy_context`).

The system handles:
- Policy document ingestion (.pdf, .docx, .txt)
- Tool-level Role-Based Access Control (`ADMIN` vs `USER` vs `UNKNOWN`)
- Secure policy updates (Admin authorization required at tool boundary)
- Strict non-hallucinated, document-grounded answers
- Safe handling of missing information
- Tool execution audit logging

---

## 🧠 Control Architecture (MCP Agent → Tool → Context)

```
User ──► Agent (LLM) ──► MCP Tool Call (Auth & Access Check Inside Tool) ──► Context ──► Agent ──► UI Output
```

- **Tool-Level Security Enforcement**: Roles are verified inside tool implementations (`mcp_core/tools.py`).
- **LLM Reasoning over Tool Outputs**: The Agent receives raw tool status, context, and explicit authorization rejection messages.
- **Native Audit Trails**: Tool invocations generate structured audit trails for enterprise compliance.

---

## ⚡ Local & Cloud AI Brain Setup (Ollama + DeepSeek-R1 32B)

This repository connects to your self-hosted **AI Brain** (e.g. Ollama running `deepseek-r1:32b` on a GCP GPU instance or local host) via standard OpenAI-compatible API endpoints.

### Step-by-Step AI Brain Deployment (GCP GPU VM)

1. **Provision Instance**: Create GCP Compute Engine VM with NVIDIA GPU (T4 / L4 / A100).
2. **Install Ollama**:
   ```bash
   curl -fsSL https://ollama.com/install.sh | sh
   ```
3. **Pull Model**:
   ```bash
   ollama run deepseek-r1:32b
   ```
4. **Configure Environment (`.env`)**:
   ```env
   AI_BRAIN_BASE_URL=http://<YOUR_GCP_VM_IP>:11434/v1
   AI_BRAIN_MODEL=deepseek-r1:32b
   AI_BRAIN_API_KEY=ollama
   ```

---

## 🚀 Usage

### 1. Installation

```bash
git clone https://github.com/your-username/mcp-agentic-control-lab.git
cd mcp-agentic-control-lab

# Install dependencies
pip install -r requirements.txt
```

### 2. Run MCP Control Center Web App
```bash
python app.py
```
Open your browser at `http://localhost:7860`.

### 3. Run Standalone MCP Native Script
```bash
python mcp_native.py
```

---

## 👨‍💻 Author

**Shubham Singh**

---

## 📜 License

MIT License
