# Triada — Educational Platform for Primary Schools

A multi-tenant learning platform where teachers manage class material and build interactive quiz games, and students learn through play — earning points, climbing leaderboards, and tracking their progress.

🔗 **Live:** https://triadak.vercel.app

> Built with React and Supabase, deployed on Vercel.

---

## What it does

**For students**
- Log in by classroom and see their subjects, materials and activities
- Play quiz games with **8 different question types**: multiple choice, true/false, written answers, fill-in-the-blank, matching pairs, image picking, accenting words, and PDF-based exercises
- Earn points, see a per-class leaderboard, and review their full game history

**For teachers**
- Create subjects, upload materials and activities per classroom
- Build questions individually or in bulk
- See per-student analytics — who's strong, who needs help, success rates
- Manage their school, students, and a personal material library
- A shared "teacher wall" for sharing ideas across schools
- A calendar with world days + personal events
- One-click ZIP backup of all their content, organised into folders

---

## Tech stack

- **Frontend:** React (React Router)
- **Backend / DB:** Supabase — PostgreSQL, Auth, Storage
- **Hosting:** Vercel
- **Other:** JSZip (client-side backup export)

---

## Architecture highlights

- **Multi-tenant by design** — every record is scoped to a school, so multiple schools use the same app in isolation.
- **Role-based access** — separate experiences for teachers (admin) and students, driven by a `profiles` table.
- **Relational data model** — schools → classrooms → subjects → activities / materials / questions, with separate tables for game sessions, answers and per-subject points.
- **Gamification engine** — points are incremented atomically via Postgres functions (`increment_points`, `increment_subject_points`), and each question is only played once per student (`question_plays`).
- **Analytics** computed from the answers table to flag strong vs. struggling students.

---

## Status & roadmap

Live and in use. Things I'd improve next:
- Move the teacher sign-up secret out of the client and into the backend
- Tighten Supabase Row Level Security policies so data is enforced server-side
- Add automated tests

---

## Some images from the site
## Screenshots

| | |
|:---:|:---:|
| <img src="https://github.com/user-attachments/assets/73e446ac-eb6f-42d0-bedf-3d8c6b2423c3" width="410"><br>*Αρχική* | <img src="https://github.com/user-attachments/assets/a059a5b4-bf30-4e37-8df8-1395099c1dec" width="410"><br>*Dashboard* |
| <img src="https://github.com/user-attachments/assets/fbff762d-9c71-4ab6-ab3b-74eff136be61" width="410"><br>*Μαθήματα* | <img src="https://github.com/user-attachments/assets/3fd840e6-5627-4f74-87c1-1eb683dece7a" width="410"><br>*Δραστηριότητες* |
| <img src="https://github.com/user-attachments/assets/71dcd019-077c-4094-81b5-2f785a86d5f8" width="410"><br>*Admin panel* | <img src="https://github.com/user-attachments/assets/1e2d0fa0-e949-44f0-a7b7-225ecc845e6c" width="410"><br>*Analytics* |
| <img src="https://github.com/user-attachments/assets/97baa2f7-3afe-4b0c-87d6-5bce9c3c0a03" width="410"><br>*Παιχνίδι* | <img src="https://github.com/user-attachments/assets/bba4ebae-ccbd-464e-9743-30eedc237cd0" width="410"><br>*Mobile view* |

*Built by Ioannis Kermizidis.*
