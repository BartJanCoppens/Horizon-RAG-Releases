# Horizon RAG

Horizon RAG is a retrieval workbench. It is for building the part of an AI assistant that looks things up: you give it your sources, ask a question, and see which passages it finds and why each one ranked where it did. Every run is kept unchanged, so you can tune the search and compare any two runs side by side.

It belongs to the Horizon suite, next to [Horizon](https://github.com/BartJanCoppens/Horizon) for presentations and [Horizon Calc](https://github.com/BartJanCoppens/Horizon-Calc-Releases) for spreadsheets. It works on **Mac**, **Windows** and **Linux**. It's free and needs no account.

> **This is an early version (0.4).** It opens on an empty project, and **Help › Open the example** opens Tax Noir's okf-be-vat pack (Belgian VAT law, word for word), indexes it and runs a question about it. You can save your work as project files, undo changes and keep versions. Adding your own sources comes in the next version; getting answers from an AI, evaluation and the Knowledge Galaxy come in later versions.

**[⬇ Download the latest version](https://github.com/BartJanCoppens/Horizon-RAG-Releases/releases/latest)**

---

## 1. Download

Open the [latest release](https://github.com/BartJanCoppens/Horizon-RAG-Releases/releases/latest), scroll down to **Assets** and click the file for your computer:

| Your computer | File to download |
|---|---|
| Mac with an Apple chip (M1, M2, M3, M4…) | `Horizon-RAG-<version>-arm64.dmg` |
| Mac with an Intel processor | `Horizon-RAG-<version>-x64.dmg` |
| Windows 10 or 11 | `Horizon-RAG-Setup-<version>-x64.exe` |
| Linux (most distributions) | `Horizon-RAG-<version>-x86_64.AppImage` |
| Linux (Ubuntu, Debian and similar, as a package) | `Horizon-RAG-<version>-amd64.deb` |

Not sure which Mac you have? Click the Apple menu  › **About This Mac**. If it says **Chip: Apple M…**, take the Apple chip file; if it says **Processor: Intel**, take the Intel file.

You can ignore the other files (`.zip`, `.blockmap`, `.yml`): the app uses them for its updates.

## 2. Install

Horizon RAG is made by one person for friends and family, so it isn't registered with Apple or Microsoft. Your computer will therefore warn you the first time you open it. That's expected; the steps below show how to get past the warning once.

### Mac

1. Open the `.dmg` file you downloaded.
2. Drag **Horizon RAG** onto the **Applications** folder in the window that appears.
3. Open **Horizon RAG** from your Applications folder (or with Spotlight).
4. macOS says it can't check Horizon RAG for malicious software and won't open it. Click **Done** (or **OK**).
5. Open **System Settings** › **Privacy & Security**, scroll down to the message about Horizon RAG and click **Open Anyway**. Confirm with your password or Touch ID, then click **Open Anyway** once more.

From then on Horizon RAG opens normally. Needs macOS 12 (Monterey) or later.

### Windows

1. Double-click `Horizon-RAG-Setup-<version>-x64.exe`.
2. If Windows shows **Windows protected your PC**, click **More info**, then **Run anyway**.
3. Horizon RAG installs by itself (no administrator rights needed) and opens. You'll find it in the Start menu afterwards.

Needs Windows 10 or 11, 64-bit.

### Linux

**AppImage** (works on most distributions):

```sh
chmod +x Horizon-RAG-*-x86_64.AppImage
./Horizon-RAG-*-x86_64.AppImage
```

Or right-click the file › **Properties** › **Permissions**, tick **Allow executing file as program**, then double-click it. On Ubuntu 22.04 or later, if it doesn't start, install FUSE first: `sudo apt install libfuse2` (on Ubuntu 24.04: `sudo apt install libfuse2t64`).

**Debian package:**

```sh
sudo apt install ./Horizon-RAG-*-amd64.deb
```

Horizon RAG then appears in your applications menu.

## 3. Getting started

Horizon RAG opens on **Retrieve**, with an empty project. Click **Open the example** (or choose **Help › Open the example**). Horizon RAG indexes Tax Noir's okf-be-vat pack of Belgian VAT law, showing each stage as it goes, then runs its question: *Does the 6 per cent rate apply to renovating a dwelling first occupied 12 years ago?*

With an OpenAI key (see **Models and keys**), passages are matched by meaning; without one, Horizon RAG matches them by their words and says so. The example starts at a similarity threshold of 0.42: move the slider and run again to see more, or fewer, passages.

Along the top is a menu bar (**File**, **Edit**, **Run**, **View** and **Help**). Below it, the window has three parts:

- **The Mixing Desk** on the left decides how passages are found and ranked:
  - six weights: semantic search, keyword search, metadata, recency, authority and diversity;
  - how many passages to rank (Top K);
  - the similarity threshold;
  - reranking on or off;
  - presets such as **Hybrid**, **Precision** and **Recall**.
  
  Move a slider, then click **Rerun** (or press ⌘↵ on a Mac, Ctrl+Enter elsewhere). **Save preset** keeps settings you like.
- **The Ranking** in the middle shows the passages the run found, best first. For each one you see its score, its parts and whether it went into the answer's context. Arrows show how far each passage moved since the run before.
- **Why this rank** on the right explains the passage you click: its text, how much each weight contributed, and the diversity penalty. **Remove from context** leaves a passage out of the next run, so you can see what changes without it.

**Run history** (the clock at the top) lists every run. Tick two to see what changed between them: settings, ranking and scores. Click a run to load its settings onto the Mixing Desk.

The toolbar on the left also has **Build**, **Explore**, **Explain**, **Evaluate** and **Sources**. These say what they will show; they arrive in later versions.

Your runs, presets and the example's index are kept on your computer, in the app, as you work. This version uses the internet only to look for updates, when you test a key in **Models & keys**, and, when you have added OpenAI's key, to index the example and embed your questions with it.

## 4. Saving your work

- **File › Save** (⌘S on a Mac, Ctrl+S elsewhere) saves the project as a `.hrag` file. The first time it asks where; after that it saves to the same file. **File › Save As…** saves a copy somewhere else.
- **File › Open…** (⌘O or Ctrl+O) opens a `.hrag` file. You can also double-click a `.hrag` file: it has Horizon RAG's own icon.
- If the project you have open has work that isn't saved to a file, **Open…** and **File › New project** ask first: save it, replace it, or cancel.
- A file that is damaged, or was made by a newer version of Horizon RAG, isn't opened, and Horizon RAG says why.

## 5. Undo and versions

- **Edit › Undo** (⌘Z or Ctrl+Z) takes back the last change to the Mixing Desk or your presets; **Edit › Redo** brings it back. Moving a slider counts as one change. Runs are never undone.
- **File › Save a version…** keeps the whole project as it is now, with a name and a note. **File › Versions…** lists them; **Restore…** brings one back (and **Undo** takes the restore back).
- Horizon RAG also keeps **safety points** by itself, just before work is replaced.

## 6. Models and keys

**File › Models & keys…** is where you choose the AI model (Claude by default) and OpenAI's embedding model, and add your keys. Keys are kept on your computer, encrypted by your system, and only sent to their own provider. **Test** checks a key with its provider, Claude's included. With OpenAI's key, its embedding model indexes the example and your questions; later versions use the AI model to answer questions.

## 7. Help

Press **F1** (or choose **Help › Horizon RAG Help**) for the help: every topic, a search, and **Show me** buttons that point at what a topic describes. **Help › Keyboard shortcuts** lists every key, and **Help › About Horizon RAG** shows which version you have.

## Updates

- **Windows** and **Linux AppImage**: new versions download in the background and install the next time you restart Horizon RAG.
- **Mac** and **Linux .deb**: Horizon RAG shows a notice when a new version is out; click **Download** and install it the same way as the first time. New versions are also on the [releases page](https://github.com/BartJanCoppens/Horizon-RAG-Releases/releases). Your work is kept.

## Uninstall

- **Mac**: drag **Horizon RAG** from Applications to the Bin.
- **Windows**: **Settings › Apps › Installed apps**, find Horizon RAG › **Uninstall**.
- **Linux**: delete the AppImage, or run `sudo apt remove horizon-rag`.

## Questions or problems

Contact Bart Jan directly, or [open an issue](https://github.com/BartJanCoppens/Horizon-RAG-Releases/issues) here.
