# Horizon RAG

Horizon RAG is a retrieval workbench. It is for building the part of an AI assistant that looks things up: you give it your sources, ask a question, and see which passages it finds and why each one ranked where it did. Every run is kept unchanged, so you can tune the search and compare any two runs side by side.

It belongs to the Horizon suite, next to [Horizon](https://github.com/BartJanCoppens/Horizon) for presentations and [Horizon Calc](https://github.com/BartJanCoppens/Horizon-Calc-Releases) for spreadsheets. It works on **Mac**, **Windows** and **Linux**. It's free and needs no account.

> **This is an early version (0.7).** It opens on an empty project. Add your own sources (files, a folder, a web page, pasted text or an OKF pack), keep them up to date with Sync now, move them to another computer with Export index… and Import index…, and ask them a question, or open the example: Tax Noir's okf-be-vat pack (Belgian VAT law, word for word). You can save your work as project files, undo changes and keep versions. Getting answers from an AI, evaluation and the Knowledge Galaxy come in later versions.

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

Horizon RAG opens on **Retrieve**, with an empty project. Click **Add source** to add your own (see **Your sources** below), or **Open the example** (also **Help › Open the example**) to try it first. For the example, Horizon RAG indexes Tax Noir's okf-be-vat pack of Belgian VAT law, showing each stage as it goes, then runs its question: *Does the 6 per cent rate apply to renovating a dwelling first occupied 12 years ago?*

With an OpenAI key (see **Models and keys**), passages are matched by meaning; without one, Horizon RAG matches them by their words and says so. The example starts at a similarity threshold of 0.42: move the slider and run again to see more, or fewer, passages.

Type any question in the field at the top (**Ask the knowledge base…**) and press **Enter** to run it.

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

The toolbar on the left also has **Sources** (see below), and **Build**, **Explore**, **Explain** and **Evaluate**, which say what they will show; they arrive in later versions.

Your runs, presets, sources' texts and indexes are kept on your computer, in the app, as you work. This version uses the internet only to look for updates, when you test a key in **Models & keys**, to read the web pages you add, and, when you have added OpenAI's key, to index your sources and embed your questions with it (their text then goes to OpenAI).

## 4. Your sources

**Sources** (the database icon in the toolbar on the left) lists your sources: how many documents and passages each holds, how often your runs retrieve it, when it was last read, and its status.

- **Add source** (on Sources, on the empty Retrieve screen, or **File › Add source…**) reads:
  - files: PDF, Word, HTML, Markdown or text, up to 50 MB each;
  - a folder: every file in it that Horizon RAG can read; images and hidden files are left out;
  - a web page, by its address;
  - pasted text;
  - an OKF knowledge pack, as a .zip or its folder.
  
  Give it a name, and say what its documents are: type, jurisdiction, year and in-force dates. **Add & index** reads, splits and indexes it, stage by stage. You can add several; they are indexed one after the other, and **Stop** stops one. If one fails, it says why, with **Try again**.
- If nothing reaches the threshold when you run, try a lower threshold: without an OpenAI key, scores are lower, and Horizon RAG suggests about 0.40.
- **Pause** leaves a source out of the next runs without forgetting it; **Resume** brings it back. **Remove** takes a source out of the project, after asking; it can't be undone.
- **Sync now** (the round arrow in a web page's or a folder's row) reads it again and indexes only what changed. For a folder, choose the folder again. If you pause or remove a source while it syncs, that stays.
- A web page can also be checked **Daily** or **Weekly** while Horizon RAG is open: choose it under **Sync** when you add the page (Weekly by default), or change it in the page's row. A check that fails is tried again later.
- **Re-index** appears at the top of Sources once your OpenAI key is set (**Models & keys**): it indexes your documents again with OpenAI's embeddings, so passages are matched by meaning rather than by words. Runs made before then read "no longer in the knowledge base".
- **Clear unused data…** at the foot of Sources deletes the indexes and documents this project no longer uses, after asking. Other project files that used them will need their sources added again.
- A source whose files couldn't all be read says which, and why, under its row.
- Your sources' texts and indexes stay on the computer that indexed them: a `.hrag` file carries their names, not their texts.
- **To move a knowledge base to another computer**, use **File › Export index…**: it saves a `.hrag-index` file (at most 256 MB) with your documents and their vectors. On the other computer, open the project's `.hrag` file, then **File › Import index…** (the empty Retrieve screen offers it too). The index goes only into the project it belongs to. Without it, adding a source there starts a new knowledge base.

## 5. Saving your work

- **File › Save** (⌘S on a Mac, Ctrl+S elsewhere) saves the project as a `.hrag` file. The first time it asks where; after that it saves to the same file. **File › Save As…** saves a copy somewhere else.
- **File › Open…** (⌘O or Ctrl+O) opens a `.hrag` file. You can also double-click a `.hrag` file: it has Horizon RAG's own icon.
- If the project you have open has work that isn't saved to a file, **Open…** and **File › New project** ask first: save it, replace it, or cancel.
- A file that is damaged, or was made by a newer version of Horizon RAG, isn't opened, and Horizon RAG says why.

## 6. Undo and versions

- **Edit › Undo** (⌘Z or Ctrl+Z) takes back the last change to the Mixing Desk or your presets; **Edit › Redo** brings it back. Moving a slider counts as one change. Runs are never undone.
- **File › Save a version…** keeps the whole project as it is now, with a name and a note. **File › Versions…** lists them; **Restore…** brings one back (and **Undo** takes the restore back).
- Horizon RAG also keeps **safety points** by itself, just before work is replaced.

## 7. Models and keys

**File › Models & keys…** is where you choose the AI model (Claude by default) and OpenAI's embedding model, and add your keys. Keys are kept on your computer, encrypted by your system, and only sent to their own provider. **Test** checks a key with its provider, Claude's included. With OpenAI's key, its embedding model indexes your sources, the example and your questions; later versions use the AI model to answer questions.

## 8. Help

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
