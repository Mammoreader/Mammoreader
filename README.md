# MammoReader – Offline Mammography Reader Study Platform

MammoReader is a browser-based tool for running blinded radiology reader studies on mammography cases. It runs **completely offline**. All questions, images and answers stay inside a folder you choose.

**Author:** Reza Dehdab

## What is in this repository

| File | Purpose |
| --- | --- |
| `index.html` | The whole application in one file – open it in the browser |
| `study-data/` | Where the study lives: `data.json` (cases, questions, answers) and `images/` |
| `icon-192.png`, `icon-512.png`, `apple-touch-icon.png`, `favicon.ico` | Icons |

Nothing has to be installed. The app is a single self-contained HTML file.

## Key features

- **Name-based login** – readers type their name; no passwords.
- **Two roles** – *Researcher* (reads cases) and *Administrator* (builds the study and exports results).
- **Two runs** 
- **Cases with up to 4 images** – shown in a 2×2 grid; click any image to enlarge it full screen.
- **Question types** – Yes/No (with optional follow-up questions shown on "Yes"), multiple choice, multi-select and free text.
- **Standard templates**
  - Run 1: *Are there any remarkable findings?* → Opacity, Microcalcification, Architectural distortion (Yes/No).
  - Run 2: *Do you think the image is AI-generated?* (always first), followed by the Run 1 questions.
- **Blinding** – image labels (e.g. real / AI) are stored for analysis but never shown to readers.
- **Randomization**
  - Optional shuffling of case order per reader.
  - Question order inside each case is always randomized (in Run 2 the AI-generated question stays first).
- **Timing** – time per question, time per case and total time per run are recorded automatically.
- **No back navigation** – once a case is submitted it cannot be changed.
- **Auto-save** – every answer is written to disk immediately.
- **Excel export** – one `.xlsx` workbook with Answers, Sessions and Cases sheets, sorted by the administrator's planned order (with the presented order kept as a separate column).

## How to run it

1. Copy this folder onto a USB stick or into a local folder (e.g. `E:\MammoReader`).
2. Open `index.html` with **Microsoft Edge** or **Google Chrome**.
3. If there is no `study-data` folder next to `index.html`, create an empty folder with that name (any empty folder works).
4. Click **Choose study folder** and select the `study-data` folder next to it. The browser asks for permission to edit files – allow it.
5. The app reads and writes:

   ```
   study-data/
     data.json   – questions, cases, sessions, answers
     images/     – uploaded case images
   ```

5. **Administrator**: click "I'm an administrator", enter the admin code (radadmin), create cases per run, upload images and review/export responses.
6. **Researcher**: enter a name, choose a run and read the cases one at a time. Progress (e.g. Case 10 / 60) is shown at the top.

You must select the folder again each time the browser is opened (browser security rule). Always use the same folder so all data stays together.

## Tips and known limits

- If the folder cannot be opened, put the app on the USB stick or in Documents rather than a OneDrive-synced Desktop.
- Managed hospital computers may block folder access in the browser; ask IT to allow it for Edge.
- Use Edge or Chrome – other browsers do not allow a web page to read and write a local folder.

## Data privacy

No data ever leaves the computer. There is no network communication, no analytics and no external storage. The study files (`data.json` and the images) are created on the machine that runs the app and are not part of this repository.
