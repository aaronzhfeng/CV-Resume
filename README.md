# CV-Resume

LaTeX sources and built PDFs for Zhaoxiang (Aaron) Feng's academic CV and industry resume.

## Current documents

| Document | Source | PDF | Use |
|---|---|---|---|
| Academic CV (one page) | [`Curriculum_Vitae/Curriculum_Vitae.tex`](Curriculum_Vitae/Curriculum_Vitae.tex) | [PDF](Curriculum_Vitae/Curriculum_Vitae.pdf) | Faculty and advisor outreach |
| Academic CV (two pages) | [`Curriculum_Vitae/variants/CV_2026_08_28_two-page.tex`](Curriculum_Vitae/variants/CV_2026_08_28_two-page.tex) | [PDF](Curriculum_Vitae/variants/CV_2026_08_28_two-page.pdf) | Research assistantship applications |
| Industry resume (one page) | [`Resume/Resume_2026_09_15.tex`](Resume/Resume_2026_09_15.tex) | [PDF](Resume/Resume_2026_09_15.pdf) | ML systems, LLM inference, and ML research internships |

## Layout

```
CV-Resume/
├── Curriculum_Vitae/
│   ├── Curriculum_Vitae.tex / .pdf   current academic CV
│   ├── variants/                     tailored CV variants
│   └── CV_archive/                   settled past versions (CV_YYYY_MM_DD.tex, PDFs in compiled/)
├── Resume/
│   ├── Resume_2026_09_15.tex / .pdf  current industry resume
│   ├── Resume.tex, Resume_v2.tex, Resume_CMU.tex   December 2025 resumes (superseded)
│   └── Resume_archive/               resume template
├── CONTENT.md                        content bank the documents draw from
└── source/                           reference material for individual projects
```

## Building

Each document is a standalone `.tex` file built with `pdflatex`:

```bash
cd Resume
pdflatex Resume_2026_09_15.tex && pdflatex Resume_2026_09_15.tex
```

The CV uses a RenderCV-derived layout. The industry resume uses
[Jake's Resume](https://github.com/jakegut/resume) (MIT), with `\pdfgentounicode=1` so the PDF parses
cleanly in applicant tracking systems.

## Conventions

- The archive holds settled versions only: a CV is copied to `CV_archive/` when it is sent or superseded,
  never while it is still being drafted.
- Build byproducts (`.aux`, `.log`, `.out`) are ignored by git.
