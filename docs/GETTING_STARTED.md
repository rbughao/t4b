<p align="center"><img src="../assets/tootsy-logo.svg" alt="Tootsy" height="72"></p>

# T4B - Tootsy for Business: install and use

T4B is a desktop AI assistant for Windows, macOS and Linux. It works with AI models running on your own computer, on your company's servers, or with cloud services such as OpenAI and Anthropic. It can read your documents, search the web, and use tools, and it asks you before it changes anything.

**Contents**
1. [What you need](#1-what-you-need)
2. [Install](#2-install)
3. [Connect an AI model](#3-connect-an-ai-model)
4. [Your first chat](#4-your-first-chat)
5. [Everyday features](#5-everyday-features)
6. [Tools: what T4B can do for you](#6-tools-what-t4b-can-do-for-you)
7. [Safety and privacy](#7-safety-and-privacy)
8. [Settings at a glance](#8-settings-at-a-glance)
9. [Troubleshooting](#9-troubleshooting)

---

## 1. What you need

- A Windows 10/11 (64-bit), macOS 11 or later (Apple silicon or Intel), or 64-bit Linux computer with about 1 GB of free disk space.
- At least one AI model. You have three options:

  | Option | Best for |
  |---|---|
  | **Local**: Ollama on your PC | Private data; it's free and works offline |
  | **Company server**: any OpenAI-compatible server on your network | Teams sharing one powerful machine |
  | **Cloud**: OpenAI, Anthropic, OpenRouter or Amazon Bedrock | The most capable models; needs an API key and is paid per use |

  Your IT team may already have one of these set up for you.

## 2. Install

Get the installer for your system from your IT team or from the [Releases page](https://github.com/rbughao/t4b/releases). The installers contain no API keys or connector credentials; you add your own after installing.

**Windows** (`T4B-Tootsy-for-Business-Setup-<version>.exe`)
1. Double-click the installer. Windows may show **"Windows protected your PC"**, because the installer isn't code-signed yet. If the file came from a source you trust, click **More info → Run anyway**.
2. Choose an install folder (the default is fine) and click **Install**.
3. Open **T4B - Tootsy for Business** from the Start menu or the desktop shortcut.

**macOS** (`…-mac-arm64.dmg` for Apple-silicon Macs, `…-mac-x64.dmg` for Intel Macs)
1. Open the `.dmg` and drag **T4B - Tootsy for Business** into **Applications**.
2. The app isn't notarized by Apple yet. The first time, **right-click (or Control-click) the app → Open → Open**.
3. If macOS says the app "is damaged and can't be opened", that's the download quarantine flag on an unsigned app. Run this once in Terminal, then open the app again:
   ```bash
   xattr -cr "/Applications/T4B - Tootsy for Business.app"
   ```

**Linux** (`…-linux-x86_64.AppImage`, or `…-linux-x64.tar.gz`)
1. Make the AppImage executable and run it:
   ```bash
   chmod +x T4B-Tootsy-for-Business-*.AppImage
   ./T4B-Tootsy-for-Business-*.AppImage
   ```
2. Or unpack the `.tar.gz` anywhere and run `t4b` inside it.
3. Some distributions need FUSE for AppImages (for example `sudo apt install libfuse2` on Ubuntu 22.04 and later).

On macOS and Linux, run-command tools use the system shell (`/bin/sh`) instead of PowerShell.

**Upgrading from AIRO.** Install over your existing copy. Your chats, notebooks, settings and saved keys carry over, because they stay in the same data folder (`%APPDATA%\airo` on Windows).

**Updates.** The installed app checks for new versions in the background. When one is ready, go to **Settings → General → Updates → Restart and update**.

## 3. Connect an AI model

A **connection** is where your models come from. On first launch T4B shows **Connect your first model**; later, use **Settings → Connections → Add connection** or **Add connection** at the bottom of the model picker. You can add as many connections as you like, including several of the same kind (for example a work and a personal OpenAI account).

Each connection is tested before you save it: you see the models it found and choose which ones appear in the picker.

### Local models with Ollama

1. Install Ollama from [ollama.com](https://ollama.com) and start it.
2. Download a model. In PowerShell, run for example:
   ```powershell
   ollama pull qwen3:4b
   ```
   Small models (1–4B parameters) are fast. Larger ones (8B and up) give better answers but need a good GPU or plenty of RAM.
3. In T4B, choose **Run free on this PC** (or **Find on this computer** in Settings → Connections). T4B finds Ollama and adds it, and your models appear in the **Model** picker. A running Ollama or LM Studio is usually found automatically when T4B starts.

### Cloud models

1. Get an API key from the service: OpenAI, Anthropic, OpenRouter, Google Gemini, Groq, Mistral, DeepSeek, xAI or Together AI, or AWS credentials for Bedrock.
2. **Add connection → Cloud accounts**, choose the service and paste the key. For the ready-made services the address is filled in for you. Keys are stored encrypted on your computer.
3. Click **Test connection**, choose which models to show, then **Add connection**. Pick a model in the sidebar.

### A company server

**Add connection → Your organisation → Company server**, then enter the server's address (for example `http://10.0.0.5:8000/v1`) and its key if it needs one. For a shared Ollama machine choose **Ollama on the network**. If the server can't list its models, tick *The server can't list its models* and type them in.

IT teams can set this up once and use **Export (without keys)**; colleagues use **Import** and add their own keys.

> **Which should I use?** Use a local model or a company server for confidential material. Use a cloud model when you need the best reasoning and the data is fine to send to that provider. The **Model Guide** in the sidebar explains the strengths of each model.

## 4. Your first chat

1. Pick a model in the sidebar's **Model** picker (models are grouped by connection; star your favourites and use the pin to make one the default for new chats). You can also switch a chat's model from its header.
2. Click **New Chat**.
3. Type your question and press **Enter**. Use **Shift+Enter** for a new line.

Under the message box:

| Button | What it does |
|---|---|
| ⚡ | Insert a **Skill**, a ready-made task such as *Summarise* or *Translate* |
| 📎 | Attach files: PDF, Word, Excel, PowerPoint, emails, images and more |
| 🌐 | Add a web page by its link |
| 📄 | Insert a prompt template (or type `/`) |
| 📁 | Give T4B access to a folder, so it can read, search and create files there |
| 🧠 | Turn the model's visible "thinking" on or off for this chat (off is faster) |
| 🔧 | Tool mode: **Auto** (only relevant tools), **On** (all tools) or **Off** |
| 🎤 | Speak your question instead of typing it |

Each reply shows the tokens used and, for cloud models, its cost. The bar at the top right shows how much of the model's memory the chat is using.

## 5. Everyday features

- **Attach documents.** Drop in PDFs (including scanned ones), Word, Excel, PowerPoint, Outlook `.msg` and `.eml` emails, EPUB, HTML, text and code. T4B extracts the text and sends it with your question.
- **Notebooks** (sidebar → Notebooks). Collections of your documents. Ask questions and get answers grounded only in those documents, with the sources named. Add files, whole folders or web pages. Turn on **Full documents** for small notebooks so the model reads everything.
- **Personas** (sidebar → Personas). Saved assistants with their own instructions, model, tools and notebook. For example, *Contract Reviewer* using a local model and your legal notebook.
- **Compare** (sidebar → Compare). Send one prompt to two or three models side by side and compare their answers, speed and cost.
- **Tagged replies.** Bookmark useful answers with colour tags, then find them again in **Tagged**.
- **Scheduler.** Run a prompt automatically, for example every Monday at 8:00. It can send results to a webhook, and it can produce a *notebook digest* that answers a question from a notebook on a schedule.
- **Quick ask.** Press **Ctrl+Shift+Space** anywhere in Windows to ask a question without switching apps. The answer opens as a new chat.
- **Code panel.** Click **Open in panel** on any code block to edit it, preview HTML, or save it to your project.
- **Projects.** Group chats by project. Project chats are saved as files inside the project's folder.
- **Status** (pulse icon in the sidebar header). See which model servers are running, what's loaded on your GPU, MCP server health, and this month's spending against your budget.

## 6. Tools: what T4B can do for you

T4B's tools let the model act, not just talk. Each tool is only offered when your message calls for it, so normal chats stay fast. You can switch tools on or off in **Settings → Tools**.

| Ask something like… | Tool used |
|---|---|
| "What's the latest on the EU AI Act?" | **Web search**, then **Read web pages**. Set up the search service first in Settings → Tools |
| "Summarise https://…" | **Read web pages** |
| "Find the invoice that mentions PO-4471" (folder granted) | **Search files** |
| "Total sales by region in sales.xlsx" | **Analyse spreadsheets** (exact SQL, no guessing) |
| "Turn this into a Word document called Q3 summary.docx" | **Create documents** (Word, PDF, Excel, HTML) |
| "What does our travel policy say about per diems?" | **Search notebooks** |
| "List my EC2 instances", "Show pods in prod" | **Run commands** (aws, kubectl, git, docker…) |
| "Get my open issues from the GitHub API" | **Call APIs**. Save the API key in Settings → Tools |
| "What's 7.5% of 1,284,000?", "Convert 30 °C to °F" | **Calculator** |
| "How many working days until 31 December?" | **Date & time** |
| "Remember that our fiscal year starts in April" | **Memory** |

You can also connect **MCP servers** (Settings → MCP Servers) for services such as Slack, Jira or databases.

## 7. Safety and privacy

- **Approval before actions.** T4B asks before any tool that could change something: running a command that isn't read-only, sending an API request other than GET, writing a file, or calling an MCP tool that makes changes. Change this in **Settings → General → Tool approval**.
- **Leak protection.** Web pages, files and command output can hide instructions aimed at the AI. Once a reply has read such content, T4B won't let the model send newly composed data anywhere (links, searches, commands, API calls) without asking you first. Keep this on in **Settings → Tools**.
- **Your data stays on your PC.** Chats, notebooks and memories are stored in `%APPDATA%\airo`, and API keys are encrypted with Windows' own protection. Back up that folder to keep a copy (**Settings → General → Your data**).
- **What leaves your PC.** Your messages and attachments go to the model provider you chose. With a local model, nothing leaves your computer except the web searches and pages you ask for.

## 8. Settings at a glance

| Tab | What's there |
|---|---|
| Connections | Add, test, edit, reorder, switch off or remove connections; find local servers; import/export without keys |
| MCP Servers | Connect external tools |
| Tools | Built-in tool switches, leak protection, web search service, API keys for API calls, memories |
| Appearance | Aurora or Graphite Teal style; light, dark or system mode; density |
| General | Tool approval, voice input, notebook search, OCR languages, quick-ask shortcut, data folder, updates |

## 9. Troubleshooting

| Problem | Try this |
|---|---|
| "No models found" | Check that Ollama (or your server) is running, then click the refresh icon next to **Model**. Check **Status** to see which servers respond |
| Local model is slow | Pick a smaller model, turn off 🧠 thinking, and check **Status** to see whether the model is on the GPU or the CPU |
| The model doesn't use a tool | Small models sometimes ignore tools. Try a larger model, set 🔧 to **On**, or name the tool ("search the web for…") |
| Web search says "no service is set up" | Choose Brave, Tavily or SearXNG in **Settings → Tools** and click **Test** |
| Scanned PDF comes out empty | The first OCR run downloads language data, so make sure you're online. Add languages in Settings → General → Reading scanned documents |
| Quick ask shortcut doesn't work | Another app may be using it. Pick another shortcut in Settings → General |
| "Windows protected your PC" when installing | The installer isn't signed yet. Use **More info → Run anyway**, but only for an installer from a trusted source |

See also: [20 ways teams use T4B](USE_CASES.md)
