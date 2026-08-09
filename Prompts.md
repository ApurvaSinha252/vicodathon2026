# ABTalks — AI-Assisted Coding Workflow Transcript

## 1. Breeth Episode

### User

Use Breeth to add an episode saying:

> Hackathon 2026 — I am preparing to build my project using an AI-assisted coding workflow.

Then confirm when the write has been created.

### Claude

The Breeth write was successfully created.

**Entity:** Hackathon 2026

**Summary:** Hackathon 2026 participant preparing to build project using an AI-assisted coding workflow.

**Narrative:** You are gearing up to transform ideas into code, leveraging AI to accelerate development and iterate rapidly.

**Stance:** Eager anticipation

**Pattern label:** Preparation

**Open question:** How will AI-assisted coding reshape the project's development timeline and success metrics?

**Source episode:** `api_1786202953234`

The original text was stored as-is.

No relational edges were extracted because the write remained a standalone entity/narrative rather than a subject-predicate-object relationship.

---

# 2. ABTalks Project Brief

### User

ABTalks runs a 60-day coding challenge for Indian college students.

Students:

* Pick a track
* Build something every day
* Maintain a public learning streak
* Submit a GitHub commit
* Submit a LinkedIn post

This daily proof of work helps students build consistency and become visible to recruiters.

Most students use the platform on their phones, late at night after college.

The product works but has never been designed.

The goal is to **Ship at Minimum Design** and build three screens.

---

## 3. Required Screens

### Landing Page — `/`

The first experience for a student who has never heard of ABTalks.

The page should provide enough:

* Trust
* Clarity
* Motivation

to encourage a student to commit to the 60-day challenge.

---

### Student Dashboard — `/dashboard`

The home screen after logging in.

It should include essentials such as:

* Current streak
* Today's task
* Progress through the challenge
* Overall completion
* Student standing or achievements

---

### Challenge Day — `/day/12`

The complete experience for a single challenge day.

A student should be able to:

* Read the day's task
* Understand what needs to be built
* Submit proof of work

  * GitHub repository/commit
  * LinkedIn post

---

# 4. Submission Requirements

Along with the repository and live deployment URL, the submission must include a Route Map.

The routes must appear in this exact order:

```text
/
/dashboard
/day/12
```

Reviewers will open every submission at a **390px mobile viewport** and automatically capture screenshots.

The route map ensures that the reviewers can find each required screen without guessing the URLs.

---

# 5. Design Requirements

The redesign should:

* Be mobile-first at 390px
* Treat desktop as a secondary consideration
* Be understandable to a student who has never heard of ABTalks
* Handle real-world edge cases
* Introduce at least one thoughtful improvement to the student experience

### Required edge cases

#### First day

A student has no streak yet.

#### Missed day

A student has missed a previous challenge day.

#### Empty profile

A student has little or no profile information.

---

# 6. Out of Scope

The project does not need:

* Authentication
* Real user accounts
* A production database
* Recruiter dashboard
* Admin panel
* ABTalkS's existing technology stack

Mocked data is sufficient.

A simple JSON file can be written manually or generated using AI.

The project can use any framework or technology that fits the AI-assisted workflow.

---

# 7. Implementation

### User

Help me build this.

### Claude

The project was assembled as three self-contained HTML pages.

The implementation also corrected relative navigation links between the pages.

The project was tested for:

* HTML validity
* JavaScript syntax
* Runtime errors
* 390px mobile rendering
* Interactions
* Demo-state switching
* Submission flow

---

# 8. Design Direction

The final design uses:

* Dark, ink-based UI
* Mobile-first layout
* Space Grotesk
* JetBrains Mono
* Inter typography
* A GitHub-inspired contribution/commit grid

The commit grid was chosen because GitHub commits are an actual part of ABTalkS's proof-of-work system rather than an invented gamification mechanism.

---

# 9. Thoughtful UX Feature

A **"Draft my post"** button was added to the Challenge Day screen.

The feature helps students turn their day's task into an editable LinkedIn caption.

The goal is to remove the friction of starting a LinkedIn post from a blank text box, particularly when students are completing their work late at night.

The feature assists the student without completely taking control of the submission.

---

# 10. Edge Cases Implemented

### First Day

A dedicated **Day 1 / New** state is available when the student has no existing streak.

### Missed Day

The dashboard includes a missed Day 7 state.

The missed day is communicated through a plain-language banner while preserving the student's previous history.

### Empty Profile

An empty-profile state provides a clear next action rather than displaying an empty or broken interface.

---

# 11. Mock Data

The project uses mocked data rather than a production database.

The mock data includes:

* Student profile
* Challenge state
* Streak information
* Missed Day 7
* Badges
* Challenge tasks for Days 11–13

A separate `mock.json` file was provided as a reference copy.

The live site embeds the same data in `src/data.js` so that the static site can operate without fetch/CORS issues.

---

# 12. Deployment

### User

How do I deploy?

### Claude

Because the project has no build step, it can be deployed as a static website.

Possible deployment options include:

* Vercel
* Netlify
* GitHub Pages

For Vercel or Netlify, the project can be deployed directly as static files.

GitHub Pages requires additional consideration because the site may be hosted under a repository subpath rather than directly at the domain root.

---

# 13. Initial Vercel Deployment Issue

The first deployment URL redirected to a Vercel login page rather than showing the application.

Possible causes included:

* Preview deployment protection
* Password/SSO protection
* A deployment that was not publicly accessible

The project was then checked through Vercel.

---

# 14. First Route Problem

The landing page loaded correctly, but:

```text
/dashboard
/day/12
```

returned 404 errors.

The issue was identified as a static-hosting routing problem.

The folder-based pages were not automatically being resolved to their respective `index.html` files.

---

# 15. Routing Fix

A `vercel.json` configuration file was added at the project root.

The configuration explicitly routes:

```text
/dashboard
```

to its corresponding page and:

```text
/day/12
```

to its corresponding page.

The project was then redeployed.

---

# 16. Final Deployment

The final deployment was:

```text
https://abtalks-1-two.vercel.app
```

The following routes were verified:

```text
/
/dashboard
/day/12
```

### Results

| Route        | Status    |
| ------------ | --------- |
| `/`          | ✅ Working |
| `/dashboard` | ✅ Working |
| `/day/12`    | ✅ Working |

The `vercel.json` routing fix resolved the previous 404 errors.

---

# 17. Deployment Protection Warning

The deployment was accessed using a Vercel sharing URL containing:

```text
?_vercel_share=...
```

The clean production URL is:

```text
https://abtalks-1-two.vercel.app
```

The `_vercel_share` token may act as a temporary access mechanism and should not be relied upon for automated screenshot systems.

Before submitting, Production Deployment Protection should be checked in Vercel to ensure that reviewers can access the routes without authentication.

---

# 18. Final Route Map

The required submission route map is:

```text
/
/dashboard
/day/12
```

---

# 19. Final Project Status

The ABTalkS redesign includes:

* ✅ Mobile-first landing page
* ✅ Student dashboard
* ✅ Challenge Day 12 page
* ✅ Mock JSON data
* ✅ First-day state
* ✅ Missed-day state
* ✅ Empty-profile state
* ✅ GitHub commit visualization
* ✅ LinkedIn draft assistance
* ✅ GitHub proof-of-work submission
* ✅ LinkedIn proof-of-work submission
* ✅ Vercel deployment
* ✅ Fixed Vercel routing
* ✅ All three required routes verified
* ✅ 390px viewport testing
* ✅ JavaScript runtime testing
* ✅ End-to-end submission flow testing

## Production URL

```text
https://abtalks-1-two.vercel.app
```
