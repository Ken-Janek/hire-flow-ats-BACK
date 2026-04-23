https://editor.swagger.io/

# Toopakkumiste ja kandidaatide haldus (ATS) - Backend

Simple REST backend for candidate tracking with CV data, interview scheduling, and current status history.

## Features

- Candidate CRUD
- CV metadata per candidate (`cvUrl` and `cvText`)
- Interview scheduling and listing
- Candidate status lifecycle (`new`, `screening`, `interview`, `offer`, `hired`, `rejected`)
- Status history for audit trail
- JSON-based local persistence (`data/db.json`)

## Run

```bash
npm install
npm run dev
```

Server runs at `http://localhost:4000`.

Swagger UI:

- `http://localhost:4000/docs`
- Raw OpenAPI JSON: `http://localhost:4000/docs/openapi.json`

## Endpoints

### Health
- `GET /health`

### Candidates
- `GET /api/candidates`
- `GET /api/candidates/:candidateId`
- `POST /api/candidates`
- `PUT /api/candidates/:candidateId`
- `POST /api/candidates/:candidateId/status`
- `POST /api/candidates/:candidateId/interviews`
- `DELETE /api/candidates/:candidateId`

### Interviews
- `GET /api/interviews`
- `GET /api/interviews?candidateId=...`
- `GET /api/interviews?from=2026-04-23T00:00:00.000Z&to=2026-04-25T00:00:00.000Z`

## Example payloads

Create candidate:

```json
{
  "firstName": "Mari",
  "lastName": "Tamm",
  "email": "mari.tamm@example.com",
  "phone": "+37255550000",
  "position": "Backend Developer",
  "cvUrl": "https://example.com/cv/mari-tamm.pdf",
  "cvText": "5+ years of Node.js and SQL experience",
  "notes": "Referred by employee"
}
```

Update status:

```json
{
  "status": "screening",
  "note": "Phone screen completed"
}
```

Schedule interview:

```json
{
  "interviewer": "Mark Recruiter",
  "type": "video",
  "scheduledAt": "2026-04-24T10:00:00.000Z",
  "durationMinutes": 60,
  "locationOrLink": "https://meet.example.com/ats-mari",
  "feedback": "Strong communication"
}
```
