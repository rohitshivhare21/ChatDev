# 🤖 ChatDev 2.0 — DevAll

**A Zero-Code Multi-Agent Platform for Developing Everything**

> This is a forked and maintained version of [OpenBMB/ChatDev](https://github.com/OpenBMB/ChatDev) by [@rohitshivhare21](https://github.com/rohitshivhare21).

---

## 📖 Overview

**ChatDev 2.0 (DevAll)** is a zero-code multi-agent orchestration platform that empowers users to rapidly build and execute customized multi-agent systems through simple YAML configuration — no coding required.

You can define agents, workflows, and tasks to orchestrate complex scenarios such as:
- 📊 Data Visualization
- 🎮 Game Development
- 🔬 Deep Research
- 🎥 Educational Video Generation
- 🗺️3D Scene Generation (with Blender)

> **ChatDev 1.0 (Legacy)** — the original Virtual Software Company simulation — is available on the [`chatdev1.0`](https://github.com/OpenBMB/ChatDev/tree/chatdev1.0) branch.

---

## 🚀 Quick Start

### 📋 Prerequisites

- **OS**: macOS / Linux / WSL / Windows
- **Python**: 3.12+
- **Node.js**: 18+
- **Package Manager**: [uv](https://docs.astral.sh/uv/)

### 📦 Installation

**1. Clone the repository:**
```bash
git clone https://github.com/rohitshivhare21/ChatDev.git
cd ChatDev
```

**2. Install Backend Dependencies (Python via `uv`):**
```bash
uv sync
```

**3. Install Frontend Dependencies (Vue 3 + Vite):**
```bash
cd frontend && npm install
```

### 🔑 Configuration

```bash
cp .env.example .env
```

Open `.env` and set your LLM provider credentials:
```
API_KEY=your_api_key_here
BASE_URL=your_base_url_here
```

### ⚡ Run the Application

**Recommended (using Makefile):**
```bash
make dev
```

Then open: [http://localhost:5173](http://localhost:5173)

**Manual:**
```bash
# Backend
uv run python server_main.py --port 6400 --reload

# Frontend (in a new terminal)
cd frontend
VITE_API_BASE_URL=http://localhost:6400 npm run dev
```

---

## 🐳 Docker Setup

```bash
# Build and run with Docker Compose
docker compose up --build
```

| Service  | URL                       |
|----------|---------------------------|
| Backend  | http://localhost:6400     |
| Frontend | http://localhost:5173     |

---

## 💡 How to Use

### 🖥️ Web Console

The DevAll interface has three main tabs:

| Tab | Description |
|-----|-------------|
| **Tutorial** | Step-by-step guides integrated into the platform |
| **Workflow** | Visual drag-and-drop canvas to design multi-agent systems |
| **Launch** | Run workflows, monitor logs, and provide human-in-the-loop feedback |

### 🧰 Python SDK

```python
from runtime.sdk import run_workflow

result = run_workflow(
    yaml_file="yaml_instance/demo.yaml",
    task_prompt="Summarize the attached document in one sentence.",
    attachments=["/path/to/document.pdf"],
    variables={"API_KEY": "sk-xxxx"}
)

if result.final_message:
    print(f"Output: {result.final_message.text_content()}")
```

Install via PyPI:
```bash
pip install chatdev
```

---

## 🌟 Featured Workflows

All workflow configs are in the `yaml_instance/` folder.

| Category | Workflow File | Example Prompt |
|----------|--------------|----------------|
| 📈 Data Visualization | `data_visualization_basic.yaml` | "Create 4–6 PNG charts for my real-estate dataset." |
| 🎮 Game Dev | `GameDev_v1.yaml` | "Design and develop a Tank Battle game." |
| 📚 Deep Research | `deep_research_v1.yaml` | "Research recent advances in LLM-based agent RL." |
| 🎓 Teaching Video | `teach_video.yaml` | "Explain what convex optimization is." |
| 🗺️ 3D Generation | `blender_3d_builder_simple.yaml` | "Build a Christmas tree." *(Requires Blender + blender-mcp)* |

---

## ⚙️ Project Structure

```
ChatDev/
├── server/          # FastAPI backend
├── runtime/         # Agent abstraction & tool execution
├── workflow/        # Multi-agent orchestration logic
├── entity/          # Agent/workflow configuration
├── frontend/        # Vue 3 Web Console
├── functions/       # Custom Python tools
├── yaml_instance/   # Runnable workflow YAML configs
├── yaml_template/   # Workflow YAML templates
└── docs/            # User guides & documentation
```

---

## 🛠️ Utility Commands

```bash
make help             # Show all available commands
make sync             # Sync YAML workflows to frontend DB
make validate-yamls   # Validate all YAML workflow files
```

---