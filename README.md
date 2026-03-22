# job-board-api-documentation

The Job Board API allows developers to manage users, job postings, and applications for a recruitment platform.
# Base URL
https://api.jobboard.com/v1

Response Format: JSON
Authentication: Bearer Token (JWT)

# Authentication

Login
Authenticate a user and receive an access token.

Endpoint
POST /auth/login

Request Body

{
  "email": "user@example.com",
  "password": "password123"
}

Response
{
  "status": "success",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "id": 1,
    "role": "recruiter",
    "name": "John Doe"
  }
}

# Register (Job Seeker)
Endpoint
POST /auth/register/jobseeker

{
  "name": "Jane Doe",
  "email": "jane@example.com",
  "password": "password123"
}

# Register (Recruiter)
POST /auth/register/recruiter

{
  "company_name": "Tech Corp",
  "email": "hr@techcorp.com",
  "password": "password123"
}

Headers (Protected Routes)
Authorization: Bearer {token}

# Users
GET /users/me
Response
{
  "id": 1,
  "name": "John Doe",
  "role": "recruiter",
  "email": "john@example.com"
}
# Jobs
Create Job (Recruiter Only)
POST /jobs

{
  "title": "Senior Frontend Developer",
  "description": "We are looking for a React expert...",
  "location": "Remote",
  "salary": "1500-3000 USD",
  "type": "full-time"
}

Response

{
  "status": "success",
  "message": "Job created successfully",
  "job_id": 12
}

Get All Jobs

GET /jobs
Query Params

?location=remote&type=full-time

[
  {
    "id": 12,
    "title": "Senior Frontend Developer",
    "company": "Tech Corp",
    "location": "Remote",
    "type": "full-time"
  }
]

Get Single Job

GET /jobs/{id}

Update Job
PUT /jobs/{id}

Delete Job
DELETE /jobs/{id}

# Applications
Apply for Job (Job Seeker)

POST /applications

{
  "job_id": 12,
  "cover_letter": "I am very interested in this role..."
}

Get Applications (Recruiter)

GET /applications?job_id=12

# Recruiter Dashboard











