# CVPilot — AI-Powered Career Assistant

CVPilot is a web platform that helps job seekers create ATS-friendly resumes, tailor them to a specific job offer, generate application emails and cover letters, and keep track of every application in one place.

> **Mission:** make job applications smarter, simpler, and more accessible through artificial intelligence.

> 🚧 **Status:** under development (academic project). The backend is built first and tested before the frontend.

## Problem

Candidates often send generic resumes, don't know why they get rejected, and lose track of their applications. CVPilot addresses each of these points.

## Features

- **Resume builder** — structured sections (experience, education, skills, projects, certifications, languages), customizable templates, PDF export
- **ATS analysis** — compatibility score between a resume and a job offer, missing keywords and improvement suggestions
- **AI writing assistant** — personalized cover letters and application emails generated from the candidate's profile and the target position
- **Application workflow** — enter the offer and the recruiter's contact, preview the email, then send it from your own Outlook (or Gmail) account via OAuth2
- **Application tracking** — statuses (draft, sent, interview, rejected, offer), deadlines and follow-up reminders
- **Admin space** — manage users and resume templates, view usage statistics

## Tech Stack

| Layer | Technologies |
|---|---|
| Backend | Java 21, Spring Boot 3, Spring Security (JWT), Spring Data JPA |
| Database | PostgreSQL, Flyway |
| Frontend | React, React Router, Axios |
| AI | LLM integration behind an `AiService` interface (swappable provider) |
| Email | Microsoft Graph API / Gmail API (OAuth2) behind a `MailSender` interface |
| API docs & tests | Swagger (springdoc-openapi), Postman, JUnit 5, Mockito |
| DevOps | Docker Compose, Git |

## Architecture

The project follows a layered architecture with a strict separation between backend and frontend.

```
cvpilot-backend/
└── src/main/java/com/cvpilot/
    ├── config/        security, CORS, OpenAPI
    ├── controller/    REST routes
    ├── dto/           request / response objects
    ├── model/         JPA entities and enums
    ├── repository/    Spring Data repositories
    ├── service/       business logic (interfaces + impl)
    ├── mapper/        entity <-> DTO
    ├── security/      JWT service and filter
    ├── integration/   ai/ and mail/ providers
    └── exception/     global error handling

cvpilot-frontend/
└── src/
    ├── api/  pages/  components/  layouts/  routes/  context/  hooks/
```

Flow: `Controller → Service → Repository`. Controllers only handle HTTP and DTOs; business logic lives in services.


## Roadmap

- [ ] Project setup, architecture, authentication (JWT)
- [ ] Resume CRUD and PDF export
- [ ] Applications and contacts management
- [ ] ATS analysis (rules + keywords + AI suggestions)
- [ ] Cover letter and email generation
- [ ] Email sending (Outlook / Gmail OAuth2)
- [ ] Admin space
- [ ] React frontend
- [ ] Automatic job matching, interview preparation (future)

## Privacy

Resumes contain personal data. CVPilot lets users delete their data, and emails are always previewed and validated by the user before sending.

## Author

**Kawtar AKRADI** — Software engineering student, ESTS Salé
