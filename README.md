# Resume Builder

A modern, browser-based resume builder built with Next.js (App Router), React 19, and Tailwind CSS 4.

Create, edit, preview, and export a clean, ATS-friendly resume — all in your browser with local storage persistence.

## 🚀 Tech Stack

- Next.js 16+ (App Router)
- React 19
- TypeScript
- Tailwind CSS 4
- LocalStorage for persistence

## ✨ Features (MVP)

- Live resume editing
- Real-time preview
- Local autosave
- JSON import/export
- Clean, print-friendly layout

## 📂 Project Structure

```
app/
  layout.tsx          # Global layout + metadata
  page.tsx            # Landing page
  builder/
    page.tsx          # Resume editor (form + preview)
  preview/
    page.tsx          # Standalone preview page
  print/
    page.tsx          # Print-optimized layout

components/
  layout/
    Navbar.tsx
    Footer.tsx
  resume/
    ResumeForm.tsx
    ResumePreview.tsx
    SectionCard.tsx
    TextField.tsx
    TextAreaField.tsx

lib/
  defaultResume.ts    # Default resume data
  resumeSchema.ts     # Zod validation schema (future-proofing)
  storage.ts          # LocalStorage utilities

types/
  resume.ts           # ResumeData TypeScript type

public/
```

## 🧠 Data Model

All resume data follows a single internal schema:

```javascript
export type ResumeData = {
  basics: {
    fullName: string;
    title: string;
    email: string;
    phone: string;
    location: string;
    website: string;
    linkedin: string;
    github: string;
  };
  summary: string;
  experience: {
    id: string;
    company: string;
    role: string;
    startDate: string;
    endDate: string;
    location: string;
    bullets: string[];
  }[];
  education: {
    id: string;
    school: string;
    degree: string;
    startDate: string;
    endDate: string;
    location: string;
  }[];
  skills: string[];
  projects: {
    id: string;
    name: string;
    link: string;
    description: string;
    bullets: string[];
  }[];
};
```

This ensures:

- Consistent state shape
- Easy JSON import/export
- Future versioning support


## 🛠 Local Development
1. 1️⃣ Clone the repository
` git clone https://github.com/kwing25/resumebuilder.git`
` cd resumebuilder`
1. Install dependencies
`npm install`
3. Run the development server
`npm run dev`

Open:
` http://localhost:3000`

## 🧩 Development Workflow

**Step 1** — Replace the Starter Page
Update `app/page.tsx` with a landing page.

**Step 2**— Define Resume Types
Create:
`types/resume.ts`
Define the `ResumeData` type.

**Step 3**— Add Default Resume Data
Create:
`lib/defaultResume.ts`
Export a starter resume object.

**Step 4**— Build the Builder Page
Create:
`app/builder/page.tsx`
Layout:
- Left column → Form
- Right column → Live Preview

**Step 5**— Add Local Persistence
Create:
`lib/storage.ts`
- saveResume()
- loadResume()
Autosave resume data on change.

**Step 6**— Add JSON Import/Export
Add buttons in builder page:
- Save JSON
- Load JSON
- Reset
Only support the internal schema initially.

## 🧪 Planned Improvements

- Zod validation for JSON import
- Drag-and-drop section reordering
- Multiple resume versions
- Theme switching
- PDF export
- AI-assisted bullet generation
- JSON Resume format compatibility

## 🖨 Print Mode

- The /print route will:
- Use a simplified layout
- Remove editor UI
- Optimize spacing for PDF
- Be ready for window.print() export

## 🗺 Roadmap

**Phase 1** — MVP
- Basic editing
- Live preview
- Local storage
- JSON import/export

**Phase 2**— UX Improvements
- Reorderable sections
- Add/remove bullets dynamically
- Cleaner mobile experience

**Phase 3** — Power Features
- Multiple saved resumes
- Resume versioning
- Theme templates
- AI tailoring
- PDF generation

## 💡 Design Philosophy

- Clean
- Minimal
- ATS-friendly
- No over-engineered dependencies
- Clear internal data schema
- Future-proof structure

## 📜 License

MIT