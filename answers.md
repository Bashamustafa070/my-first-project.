# Day 5 Technical Writing Assignment — Answers

**Student:** ______mustafa basha________________________  
**Date:** ______________________25\11\2026________  

## Assignment Overview

The purpose of this assignment is to practise writing technical documentation for different audiences and purposes. The work covers:

1. A user-facing procedure that explains how to complete a technical task.
2. An API reference entry that explains how a developer can use an API endpoint.
3. A brief technical report section / review of the documentation, including peer feedback where required by the class activity.

The documentation should be clear, accurate, well organised, consistent, and understandable to its intended audience.

---

# Exercise A: User-Facing Procedure

## Question / Task

Choose one technical task and write a procedure that helps a beginner complete it. The procedure must include:

- Prerequisites: what the user needs before starting.
- Numbered steps: each step should describe one action and state the expected result.
- Screenshot description: explain what screenshot(s) would demonstrate successful completion.
- Troubleshooting: describe at least one common error and how to resolve it.

## Selected Topic

**Creating a GitHub repository and making the first commit using Git and PowerShell.**

## 1. Purpose

This procedure explains how a beginner can create a GitHub repository, create a local project folder, initialise Git, add a README file, commit the file, connect the local project to GitHub, and push the first commit to the remote repository.

## 2. Prerequisites

Before starting, the user needs:

1. A computer running Windows.
2. An internet connection.
3. A GitHub account.
4. Git installed on the computer.
5. Visual Studio Code installed (or another text editor).
6. Basic knowledge of opening folders and using Windows PowerShell.

**Check that Git is installed:** Open PowerShell and run:

```powershell
git --version
```

**Expected result:** PowerShell displays the installed Git version. If it says that `git` is not recognised, install Git for Windows and reopen PowerShell.

## 3. Procedure

### Part A: Create a repository on GitHub

**Step 1 — Open GitHub.**  
Action: Open a web browser and go to https://github.com.  
Expected result: The GitHub home page appears.

**Step 2 — Sign in.**  
Action: Sign in using your GitHub account.  
Expected result: Your GitHub dashboard appears.

**Step 3 — Start a new repository.**  
Action: Select the option to create a new repository.  
Expected result: The repository creation form appears.

**Step 4 — Enter the repository name.**  
Action: Enter `my-first-project` as the repository name.  
Expected result: The repository name is entered in the form.

**Step 5 — Choose repository visibility.**  
Action: Select **Public**.  
Expected result: The repository is configured to be publicly accessible.

**Step 6 — Create the repository.**  
Action: Select **Create repository**.  
Expected result: GitHub displays the new repository page.

### Part B: Create the local project

**Step 7 — Open PowerShell.**  
Action: Open Windows PowerShell.  
Expected result: A PowerShell prompt appears.

**Step 8 — Create the project folder.**  
Action: Run:

```powershell
mkdir my-first-project
```

Expected result: A folder named `my-first-project` is created in the current directory.

**Step 9 — Enter the project folder.**  
Action: Run:

```powershell
cd my-first-project
```

Expected result: The PowerShell prompt shows that the current directory is `my-first-project`.

**Step 10 — Initialise Git.**  
Action: Run:

```powershell
git init
```

Expected result: Git initialises an empty repository in the project folder.

**Step 11 — Create the README file.**  
Action: Run:

```powershell
New-Item README.md
```

Expected result: A file named `README.md` appears in the project folder.

**Step 12 — Open the project in Visual Studio Code.**  
Action: Run:

```powershell
code .
```

Expected result: Visual Studio Code opens the project folder.

**Step 13 — Add project information.**  
Action: Enter a project title and a short description in `README.md`, then save the file.  
Expected result: The README contains an introduction to the project.

### Part C: Commit and publish the project

**Step 14 — Stage the README file.**  
Action: In PowerShell, run:

```powershell
git add README.md
```

Expected result: Git stages the README file for the next commit.

**Step 15 — Create the first commit.**  
Action: Run:

```powershell
git commit -m "Initial project commit"
```

Expected result: Git records the staged file in a commit.

**Step 16 — Connect the local repository to GitHub.**  
Action: Run:

```powershell
git remote add origin https://github.com/Bashamustafa070/my-first-project.git
```

Expected result: The GitHub repository is configured as the local repository's remote named `origin`.

**Step 17 — Set the branch name.**  
Action: Run:

```powershell
git branch -M main
```

Expected result: The current branch is named `main`.

**Step 18 — Push the commit to GitHub.**  
Action: Run:

```powershell
git push -u origin main
```

Expected result: Git uploads the commit to GitHub, and the `main` branch is connected to the remote branch.

## 4. Screenshot Description

The following screenshots demonstrate the completed procedure:

1. **GitHub repository screenshot:** Shows the public repository named `my-first-project`, the `main` branch, the `README.md` file, and the commit history.
2. **PowerShell screenshot:** Shows the successful `git push -u origin main` command and output confirming that the `main` branch was pushed to GitHub.
3. **Visual Studio Code screenshot (optional):** Shows the project folder and the completed `README.md` file.

Screenshots should be genuine captures of the completed work. They can be placed in a folder named `screenshots` in the project repository if the instructor requests them.

## 5. Troubleshooting

**Problem: `git` is not recognised as a command.**

**Cause:** Git may not be installed, or its installation directory may not be included in the system PATH.

**Solution:**

1. Install Git for Windows from https://git-scm.com/download/win.
2. Close and reopen PowerShell.
3. Run `git --version` again.
4. If the command still fails, check that Git was added to the Windows PATH during installation.

**Additional issue encountered: Remote repository already contains a commit.**

If GitHub has an initial README or another commit that is not in the local repository, the first push may be rejected because the remote contains work that is missing locally.

**Solution:** Fetch and integrate the remote history, resolve any merge conflicts carefully, commit the resolution if required, and then push again. Do not overwrite remote work without checking it first.

## 6. Result

The procedure creates a local Git repository, records the README in a commit, connects the local repository to GitHub, and publishes the project to the public GitHub repository:

https://github.com/Bashamustafa070/my-first-project

---

# Exercise B: API Reference Entry

## Question / Task

Write an API reference entry for a hypothetical endpoint that allows an authenticated user to create a new task in a project management application.

A task has the following information:

- Title
- Optional description
- Assignee (user ID)
- Due date
- Priority: low, medium, or high

The API documentation must include:

1. HTTP method and endpoint path.
2. A plain-language description of what the endpoint does.
3. Path, query, and request-body parameters.
4. For each parameter: name, type, whether it is required or optional, and its description.
5. Required request headers, including authentication.
6. All possible response codes and an explanation of each.
7. An example JSON request.
8. An example successful JSON response.

## API Name: Task Manager API

### 1. Endpoint Overview

**HTTP Method:** `POST`

**Endpoint:**

```http
POST /api/v1/projects/{project_id}/tasks
```

**Description:**

This endpoint allows an authenticated user to create a new task inside a specific project. The user submits the task title, optional description, assignee ID, due date, and priority. The API validates the request and creates the task when the supplied information is valid and the user has permission to create tasks in the project.

### 2. Path Parameters

Path parameters are values included directly in the endpoint URL.

| Parameter | Type | Required | Description |
|---|---|---|---|
| `project_id` | Integer | Yes | The unique identifier of the project in which the task will be created. |

**Example path:**

```http
/api/v1/projects/101/tasks
```

In this example, `101` is the project ID.

### 3. Query Parameters

This endpoint does not require query parameters. All task information is supplied in the JSON request body.

### 4. Request Body Parameters

The request body must be JSON.

| Parameter | Type | Required | Description |
|---|---|---|---|
| `title` | String | Yes | The name of the task. It must not be empty. |
| `description` | String | No | Additional information about the task. |
| `assignee_id` | Integer | Yes | The ID of the existing user assigned to the task. |
| `due_date` | String (`YYYY-MM-DD`) | Yes | The date by which the task should be completed. |
| `priority` | String | Yes | The task priority. Accepted values are `low`, `medium`, and `high`. |

**Validation rules:**

- `title` must be present and contain non-whitespace text.
- `description` may be omitted.
- `assignee_id` must identify an existing user who can be assigned to the task.
- `due_date` must use the `YYYY-MM-DD` date format.
- `priority` must be exactly one of `low`, `medium`, or `high`.
- `project_id` must identify a project that the authenticated user is allowed to access.

### 5. Request Headers

| Header | Required | Description |
|---|---|---|
| `Authorization` | Yes | Supplies the user's access token using the Bearer token scheme. |
| `Content-Type` | Yes | Identifies the request body format. Must be `application/json`. |
| `Accept` | No | Indicates the response format the client can accept. Use `application/json`. |

**Example headers:**

```http
Authorization: Bearer your_access_token
Content-Type: application/json
Accept: application/json
```

The token shown here is a placeholder. A real request must use a valid access token.

### 6. Example Request

**HTTP request:**

```http
POST /api/v1/projects/101/tasks HTTP/1.1
Host: api.taskmanager.com
Authorization: Bearer your_access_token
Content-Type: application/json
Accept: application/json
```

**JSON request body:**

```json
{
  "title": "Complete Database Assignment",
  "description": "Finish the SQL queries and submit the assignment.",
  "assignee_id": 25,
  "due_date": "2026-12-05",
  "priority": "high"
}
```

### 7. Successful Response

**Status code:** `201 Created`

**Description:** The task was successfully created.

**Example JSON response:**

```json
{
  "success": true,
  "message": "Task created successfully",
  "data": {
    "id": 501,
    "project_id": 101,
    "title": "Complete Database Assignment",
    "description": "Finish the SQL queries and submit the assignment.",
    "assignee_id": 25,
    "due_date": "2026-12-05",
    "priority": "high",
    "status": "pending",
    "created_at": "2026-11-25T09:00:00Z",
    "updated_at": "2026-11-25T09:00:00Z"
  }
}
```

**Response field notes:**

- `success` indicates whether the request succeeded.
- `message` provides a human-readable result.
- `data.id` is the ID assigned to the newly created task.
- `data.project_id` identifies the project containing the task.
- The remaining fields describe the saved task.
- `status` is initially set to `pending`.
- `created_at` and `updated_at` record the creation and last-update timestamps in ISO 8601 format.

### 8. HTTP Response Codes

The following response codes are part of this hypothetical API design.

| Status Code | Name | Explanation |
|---|---|---|
| `201` | Created | The task was successfully created. |
| `400` | Bad Request | The request is malformed or contains invalid request syntax. |
| `401` | Unauthorized | The authentication token is missing, invalid, or expired. |
| `403` | Forbidden | The authenticated user does not have permission to create a task in the specified project. |
| `404` | Not Found | The specified project or assignee cannot be found. |
| `409` | Conflict | The request conflicts with an existing resource or a project rule that prevents creation. |
| `415` | Unsupported Media Type | The request uses a content type other than the supported JSON format. |
| `422` | Unprocessable Entity | The JSON is readable, but one or more field values fail validation. |
| `500` | Internal Server Error | An unexpected error occurred while processing the request. |

### 9. Example Error Response

For example, if the priority value is not supported, the API may return `422 Unprocessable Entity`.

```json
{
  "success": false,
  "message": "Validation failed",
  "errors": {
    "priority": [
      "Priority must be low, medium, or high."
    ]
  }
}
```

### 10. Summary

The Create Task endpoint uses the HTTP `POST` method to add a task to a project. It requires authentication and a valid project ID. The request body supplies the task details in JSON format. If the request is valid and the user is authorised, the API returns `201 Created` and the newly created task. Otherwise, it returns an appropriate error status code.

**Important note:** This is a hypothetical API designed for the assignment. The endpoint, example domain, response structure, and response codes are proposed documentation examples; they are not claims about an existing production API.

---

# Assignment Submission Checklist

Use this checklist to verify that the work is ready to submit.

## Exercise A — User-facing procedure

- [ ] A technical task was selected.
- [ ] Prerequisites were listed.
- [ ] Numbered instructions were provided.
- [ ] Each numbered step describes one action and its expected result.
- [ ] Screenshot(s) were captured or their required content was identified.
- [ ] At least one common error and its solution were documented.

## Exercise B — API reference

- [ ] HTTP method and endpoint path were included.
- [ ] The endpoint purpose was explained in plain language.
- [ ] Path parameters were documented.
- [ ] Query parameters were documented, including stating when none are required.
- [ ] Request-body parameters include names, types, required/optional status, and descriptions.
- [ ] Required headers, including authentication, were documented.
- [ ] Response codes and explanations were included.
- [ ] An example JSON request was provided.
- [ ] An example successful JSON response was provided.

## Final submission

- [ ] Both exercises are included in this `answers.md` file.
- [ ] The document has been proofread for spelling, grammar, consistency, and formatting.
- [ ] Any screenshots required by the instructor are included or attached as instructed.
- [ ] The file is saved in the correct assignment folder or repository.
- [ ] The submission follows the instructor's required submission method.

## What to Submit

Submit the completed **`answers.md`** file containing Exercise A and Exercise B.

Also include the Exercise A screenshots if the instructor requires screenshots as separate evidence or as files in the project. If the assignment platform asks for a repository link instead of a file upload, provide the required public GitHub repository link:

https://github.com/Bashamustafa070/my-first-project

**Peer review:** If your class activity requires you to exchange work with a classmate, share this document for review, provide constructive feedback on clarity and completeness, and make any agreed corrections before final submission. The exact peer-review questions or form were not included in the assignment details available while preparing this document, so follow the instructor's separate peer-review instructions if provided.
