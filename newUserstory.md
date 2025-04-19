# 👗 Fashion Design Web App – User Stories with Tech Stack

---

## 🏠 Epic 1 — Welcome & Style Selection

| ID  | User Story | Acceptance Criteria | Tech Stack |
|----|-------------|---------------------|------------|
| **1.1** | **Start Journey** – As a *user* I want a landing page with a **“Start Designing”** CTA so I can enter the workflow. | • Splash text & brief intro<br>• Button routes to `/design` | **Front‑end:** Tailwind CSS layout + Alpine.js or React router |
| **1.2** | **Choose Garment Style** – After clicking start, I want to pick a base style (*Shift dress, A‑line, T‑shirt, etc.*) so the engine knows which block to draft. | • Card / dropdown list of styles<br>• Selection stored in state/session for later API calls | **UI:** Headless UI + Alpine.js/React<br>**State:** Pinia/Zustand or Alpine store |

---

## 🎨 Epic 2 — Design Input (Canvas & Upload)

| ID  | User Story | Acceptance Criteria | Tech Stack |
|----|-------------|---------------------|------------|
| **2.1** | **Sketch Design** – As a user I want a drawing canvas with pen, erase, color picker, undo, clear, and save. | • Canvas accepts mouse/stylus<br>• Toolbar controls work<br>• “Save” stores SVG/PNG in browser memory | **Canvas:** **Konva.js** |
| **2.2** | **Upload Existing Sketch** – I want to drag‑and‑drop a PNG/JPG and see it on the canvas for optional edits. | • Drag‑and‑drop zone validates file type ≤ 5 MB<br>• Image placed as editable object on Konva canvas | **Upload:** Dropzone.js + Konva image import |

*(The system **does not parse** the sketch; it’s only a visual aid for the user.)*

---

## 📏 Epic 3 — Body Measurements

| ID  | User Story | Acceptance Criteria | Tech Stack |
|----|-------------|---------------------|------------|
| **3.1** | **Manual Measurement Entry** – I want to enter chest, waist, hips, shoulder, neck, arm length, and dress length with inline validation. | • Numeric `input[type="number"]`, min/max checks<br>• Tooltip images show how to measure each body part | **UI:** Tailwind CSS forms + Alpine reactive validation |
| **3.2** | **AI Camera Capture (Optional)** – I want to snap a photo, input my height, and get auto‑estimated measurements. | • Camera permission & live preview<br>• POST image + height to `/api/estimate`<br>• Fields auto‑populate on success | **Front‑end:** getUserMedia + vanilla JS<br>**Back‑end:** Flask + MediaPipe Pose + OpenCV |

---

## 📐 Epic 4 — Pattern Drafting

| ID  | User Story | Acceptance Criteria | Tech Stack |
|----|-------------|---------------------|------------|
| **4.1** | **Generate Base Pattern** – After I hit “Generate Pattern” the system creates front/back bodice (and sleeve if needed) sized to my measurements & chosen style. | • Spinner while loading<br>• `/api/pattern` returns SVG pieces<br>• Pieces render in preview panel | **Back‑end:** Flask/FastAPI + FreeSewing core (JS via PyMiniRacer) *or* pure‑Python formulas |
| **4.2** | **Adjust Pattern Details** – I can tweak neckline depth, hem flare, sleeve length, etc., with sliders and see updates instantly. | • Sliders send PATCH / query params<br>• SVG rerenders in ≤ 1 s | **Live update:** Fetch + Alpine/React state<br>**SVG manipulation:** @svgdotjs/svg.js |

---

## 🧵 Epic 5 — Preview & Fit Checks

| ID  | User Story | Acceptance Criteria | Tech Stack |
|----|-------------|---------------------|------------|
| **5.1** | **Pattern Viewer** – I want to zoom/pan each piece (with seam allowance & grainline) to inspect before download. | • SVG viewport with mouse‑wheel zoom<br>• Notches & labels visible at 100 % | **SVG UI:** svg‑pan‑zoom |
| **5.2** | **Simple 3‑D Mockup** – I want to see a basic 3‑D drape on a mannequin to gauge silhouette. | • “Preview 3‑D” loads GLB avatar + pattern texture<br>• Rotate/zoom controls | **3‑D:** Babylon.js (placeholder cloth projection) |

---

## ✅ Epic 6 — Export & Project Management

| ID  | User Story | Acceptance Criteria | Tech Stack |
|----|-------------|---------------------|------------|
| **6.1** | **Download Pattern** – I can export the pattern as tiled PDF and/or raw SVG. | • “Download PDF” triggers `/api/export/pdf` (ReportLab / pdfkit tiling)<br>• “Download SVG” direct link | **Back‑end:** ReportLab (PDF) + svglib |
| **6.2** | **Save Project (Optional Auth)** – If I’m logged in, my sketch, measurements, and patterns are stored so I can return later. | • POST to `/api/projects` creates DB row<br>• Dashboard lists saved designs | **Auth + DB:** Flask‑Login + SQLAlchemy + PostgreSQL/S3 |

---

## 🛠️ Libraries Cheat‑Sheet

| Purpose | Library |
|---------|---------|
| Drawing Canvas | **Konva.js** |
| File Upload | Dropzone.js |
| UI Components | Tailwind CSS + Headless UI (or DaisyUI) |
| Front‑end State | Alpine.js (light) *or* React + Zustand |
| API Server | Flask *or* FastAPI |
| Pattern Drafting | FreeSewing core (JS) wrapped, *or* custom Python formulas |
| SVG → PDF | ReportLab + svglib |
| 3‑D Preview | Babylon.js |
| AI Measurement | MediaPipe Pose + OpenCV |
