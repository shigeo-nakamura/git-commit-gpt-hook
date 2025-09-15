# git-commit-gpt-hook

💡 A Git hook that suggests commit messages (Japanese + English) using OpenAI's GPT models.

## Features
- Generates **concise commit message suggestions** from your staged `git diff`
- Provides both **Japanese** and **English** messages
- Works with any Git project (just copy the hook)
- Requires only `bash`, `curl`, and `jq`

---

## Setup

1. Clone this repository (or just copy the hook script):
   ```bash
   git clone https://github.com/YOURNAME/git-commit-gpt-hook.git
   ```

2. Copy the hook to your project:
   ```bash
   cp git-commit-gpt-hook/prepare-commit-msg /path/to/your/project/.git/hooks/
   chmod +x /path/to/your/project/.git/hooks/prepare-commit-msg
   ```

3. Set your OpenAI API key:
   - **fish**
     ```fish
     set -Ux OPENAI_API_KEY "sk-xxxxxxxx"
     ```
   - **bash/zsh**
     ```bash
     export OPENAI_API_KEY="sk-xxxxxxxx"
     ```

4. Install `jq` (required for parsing JSON):
   ```bash
   sudo apt install jq   # Ubuntu/Debian
   brew install jq       # macOS
   ```

---

## Usage

Stage your changes and run:

```bash
git add .
git commit
```

When the commit editor opens, you'll see a suggested message at the top:

```
# --- ChatGPT Suggested commit message ---
# 日本語: サービス層の依存関係を修正
# English: Fix service layer imports
```

You can edit or replace it before saving.

---

## Notes
- Uses [OpenAI Chat Completions API](https://platform.openai.com/docs/api-reference/chat) (`gpt-4o-mini` by default).
- The hook adds suggestions as **comments**, so your final commit message is always under your control.
- Compatible with Linux/macOS. (Windows WSL works too)

---

## License
MIT
