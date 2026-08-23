# ClinicFlow Workflow Website — Technical Specification

**Project:** ClinicFlow Workflow Site Map
**Source:** `E:/ClinicFlow/ClinicFlow_TRD_with_Workflow_Diagrams.docx`
**Output folder:** `E:/ClinicFlow/Workflow Site map/`
**Task:** Build a hand-drawn-looking HTML/CSS website that visualizes the ClinicFlow workflow diagrams from the TRD.

---

## What This Website Is

A single-page (or multi-section) website that presents the ClinicFlow workflow diagrams as a visual site map. The aesthetic must feel hand-drawn: sketchy lines, slight wobble, paper-like background, imperfections. Think Excalidraw-meets-a-notebook.

---

## Workflow Content to Visualize (from TRD)

The website must include all of these workflow sections, adapted into visual diagrams:

### 1. Incoming Message Workflow (TRD §6.1)
Patient WhatsApp → WhatsApp Cloud API (webhook) → FastAPI Webhook Handler / Validation-Parser → Message Processing → AI Intent Service → Business Logic → Database → Response Generator → WhatsApp Cloud API → Patient

### 2. Outgoing Message Workflow (TRD §6.2)
FastAPI → Response Generator → WhatsApp Cloud API → Patient WhatsApp

### 3. AI Processing Pipeline (TRD §7.1)
Incoming WhatsApp Message → Language/Intent Understanding → Entity Extraction (doctor/date/etc.) → Validate AI Output (structured JSON) → Backend Business Logic → Database Query/Action → Natural Response Generation → WhatsApp

### 4. Clinic Onboarding Workflow (TRD §11.1)
Clinic Owner → Create Account → Clinic Details → Add Doctors + Schedules → Add Services + Fees → Add FAQs → Registration Configuration → Review & Test → Activate Bot

### 5. Patient Registration State Machine (TRD §12.1)
Patient: "I need an appointment" → appointment_booking intent detected → Ask configured registration fields → Validate input → Store/update patient record → Create pending appointment → Dashboard update

### 6. Appointment Confirmation Flow (TRD §13.1)
Patient → Request appointment → AI extracts doctor/date/time → Backend validates request → Check doctor schedule → (if unavailable: suggest alternatives) → (if available: create PENDING) → Clinic Dashboard → Owner confirms → Appointment CONFIRMED → Patient receives confirmation

### 7. Financial Workflow (TRD §14.1)
Clinic Owner → Enter Revenue / Enter Expense → Transactions Database → Reporting Service → Revenue - Expenses = Net Income
Monthly Report: Revenue | Expenses | Net Income | New Patients | Total Appointments | Completed | Cancelled

---

## Hand-Drawn Aesthetic Requirements

The website MUST look hand-drawn. Apply the following:

1. **Paper-like background** — off-white/cream with subtle texture. Not pure white.
2. **Sketchy borders** — rectangles should look hand-drawn, not sharp CSS rectangles. Use SVG filters or CSS techniques to create wobble/roughness.
3. **Hand-drawn arrows and connectors** — flow arrows between steps should look sketched, not clean straight lines.
4. **Slightly irregular typography** — use a handwritten/rough font (Google Fonts: "Patrick Hand", "Caveat", "Indie Flower", or "Kalam"). If a font isn't available, fall back gracefully.
5. **Subtle imperfections:**
   - Slight rotation on elements (±1-2 degrees)
   - Uneven shadow/offset
   - Rough stroke edges on SVG paths
   - Slight color variation between similar elements
6. **Color palette** — use the TRD's conceptual colors but in a hand-drawn washed style:
   - Patient/WhatsApp: light teal/cyan
   - WhatsApp Cloud API: light pink/magenta
   - FastAPI Backend: light green
   - AI Service/Groq: light orange
   - Database: light blue
   - Dashboard: light purple
   - Error/safety boxes: light red
   - Flow titles: dark yellow/amber
7. **Feel** — like a whiteboard sketch or notebook diagram, not a corporate flowchart tool.

---

## Technical Requirements

1. **Single HTML file** with embedded CSS (and inline SVG if needed). No external dependencies except Google Fonts.
2. **Responsive** — works on desktop and mobile (stack vertically on small screens).
3. **No JavaScript required** for the core visual, but smooth scrolling between sections is fine.
4. **Each workflow is a visual diagram**, not just text. Use boxes, arrows, and connecting lines.
5. **Navigation** — a simple top navigation bar (hand-drawn style) that scrolls to each workflow section.
6. **Title section** at the top: "ClinicFlow — Workflow Site Map" with subtitle "AI-Powered WhatsApp Automation & Clinic Management Platform".

---

## File Output

- Save as `index.html` in `E:/ClinicFlow/Workflow Site map/`
- Optionally add a `styles.css` if separation is cleaner, but inline is fine too.

---

## Definition of Done

- [ ] `index.html` opens in a browser and shows all 7 workflow diagrams
- [ ] Website looks hand-drawn (sketchy lines, paper bg, handwritten font, imperfections)
- [ ] Each workflow is a visual diagram with boxes and connecting arrows
- [ ] Navigation works and scrolls to sections
- [ ] Responsive on mobile
- [ ] No console errors
- [ ] Runs offline (no external assets except Google Fonts — and degrades gracefully if offline)
