# Resumes and cover letters (Jobs)

```text
get_job_details → get_job_keywords → create_resume / create_cover_letter
```

- Inputs: candidate resume/profile text + `job_id` + keywords as `job_context`
- Hiring-ready output omits unknowns. Do not invent employers, schools, or metrics
- Never invent employers, schools, metrics, or skills not in the source resume
- Attach generated docs to hosted apply when the API accepts them
- Scope: `agent:tools` (+ `jobs:read` for details/keywords)

Docs: [Create resumes](https://docs.worklittle.com/jobs/api/create-resumes) · [Create cover letters](https://docs.worklittle.com/jobs/api/create-cover-letters) · [Prompting for applications](https://docs.worklittle.com/use-cases/prompting-applications)
