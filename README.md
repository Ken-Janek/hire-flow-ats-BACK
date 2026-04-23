# Toopakkumiste ja kandidaatide haldus (ATS) - OpenAPI spetsifikatsioon

See repositoorium sisaldab ATS projekti OpenAPI 3.0.3 kirjeldust JSON-formaadis.

## Failid

- `.gitignore`
- `README.md`
- `openapi.json`

## Mida API katab

- Kandidaatide haldus (CRUD)
- CV andmete kirjeldus (`cvUrl`, `cvText`)
- Intervjuude planeerimine ja nimekiri
- Kandidaadi staatuse haldus (`new`, `screening`, `interview`, `offer`, `hired`, `rejected`)
- Staatuse ajaloo kirjeldus

## Kuidas Swaggeris avada

1. Ava [Swagger Editor](https://editor.swagger.io/)
2. Vali `File -> Import file`
3. Impordi `openapi.json`

Alternatiivina saab kasutada ka GitHub Raw linki:

- `https://raw.githubusercontent.com/Ken-Janek/hire-flow-ats-BACK/main/openapi.json`

## Endpointide ülevaade

### Health
- `GET /health`

### Candidates
- `GET /api/candidates`
- `GET /api/candidates/{candidateId}`
- `POST /api/candidates`
- `PUT /api/candidates/{candidateId}`
- `POST /api/candidates/{candidateId}/status`
- `POST /api/candidates/{candidateId}/interviews`
- `DELETE /api/candidates/{candidateId}`

### Interviews
- `GET /api/interviews`
- `GET /api/interviews?candidateId=...`
- `GET /api/interviews?from=2026-04-23T00:00:00.000Z&to=2026-04-25T00:00:00.000Z`
