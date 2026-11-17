# PlaceMate – MCP-Powered Campus Placement Assistant

A Python-based placement management assistant built using Model Context Protocol (MCP), SQLite, and MCP Inspector.

## 1. Project Overview

PlaceMate is an MCP-powered application that helps users manage basic campus placement activities.

The project demonstrates how backend functionality can be exposed to MCP-compatible AI clients through the Model Context Protocol. It supports job searching, application management, job detail retrieval, and interview preparation.

The application is developed using Python, with SQLite for local data storage. VS Code is used for development, and MCP Inspector is used to test the server functionality.

## 2. Technologies Used

| Technology | Purpose |
|---|---|
| Python | Backend development |
| MCP Python SDK | MCP server implementation |
| SQLite | Local database |
| uv | Dependency management |
| VS Code | Development environment |
| MCP Inspector | Testing MCP tools, resources, and prompts |

## 3. System Architecture

PlaceMate follows an MCP client-server architecture.

- MCP Client: Communicates with the MCP server.
- MCP Server: Exposes tools, resources, and prompts.
- Database Layer: Handles database operations.
- SQLite: Stores job and application records.
- MCP Inspector: Provides an interface to connect to and test the MCP server.

## 4. Project Workflow

```text
        USER REQUEST
              |
              v
        MCP INSPECTOR
          (Testing)
              |
              v
         MCP CLIENT
              |
              v
     PLACEMATE MCP SERVER
              |
        +-----+------+
        |     |      |
        v     v      v
      TOOLS RESOURCE PROMPT
        |     |      |
        +-----+------+
              |
              v
       PYTHON FUNCTIONS
              |
              v
        SQLITE DATABASE
              |
              v
        RESULT RETURNED
              |
              v
         MCP INSPECTOR
```

Workflow: The MCP server is started from the VS Code terminal and connected to MCP Inspector. Requests are tested through the Inspector, which communicates with the server. The server executes the relevant Python functionality, interacts with SQLite when required, and returns the results.

## 5. Core MCP Features

### Tools

| Tool | Description |
|---|---|
| `search_jobs` | Searches sample jobs based on keywords and location. |
| `add_application` | Records a student's job application. |
| `list_applications` | Retrieves a student's application history. |
| `update_status` | Updates an application's status. |

### Resource

`jobs://{job_id}`

Retrieves details of a specific job using its job ID.

Example: `jobs://1`

### Prompt

`interview_prep`

Generates interview preparation instructions based on the job title and company. It guides the AI to ask technical questions one at a time and provide feedback.

## 6. Database

The project uses SQLite for local data storage.

Database: `placemate.db`

It maintains:

- Jobs: Job ID, title, company, location, and required skills.
- Applications: Application ID, student name, job ID, and application status.

Python database functions handle searching, inserting, retrieving, and updating records.

## 7. Project Structure

```text
placemate/
├── server.py       # MCP server, tools, resource and prompt
├── database.py     # Database operations
├── models.py       # Data models and application logic
├── placemate.db    # SQLite database (local)
├── pyproject.toml  # Project configuration
├── uv.lock         # Dependency lock file
├── .gitignore
└── README.md
```

## 8. Setup and Execution

Prerequisites: Python 3.11+, uv, and VS Code.

Open the project directory in VS Code and run:

```bash
cd C:\Users\jeevi\Documents\placemate

# Install dependencies
uv sync

# Start MCP Inspector
uv run mcp dev server.py
```

The MCP Inspector interface can be used to connect to the server and test its available tools, resources, and prompts.

## 9. Testing

All core functionalities were tested using MCP Inspector.

| Test | Result |
|---|---|
| Job search | Passed |
| Add application | Passed |
| List applications | Passed |
| Update application status | Passed |
| Job resource retrieval | Passed |
| Interview preparation prompt | Passed |

Sample scenario: Retrieved the Junior Python Developer position at TechNova in Chennai, added an application for Asha, viewed the application history, and updated its status to Shortlisted.

## 10. Learning Outcomes

Through this project, I gained practical experience in:

- Building an MCP server using Python.
- Exposing backend functions as MCP tools.
- Integrating SQLite with Python.
- Understanding MCP tools, resources, and prompts.
- Testing MCP functionality using MCP Inspector.
- Managing Python dependencies using uv.

## 11. Limitations and Future Enhancements

Current limitations:

- Uses sample job data instead of live vacancies.
- Uses a local SQLite database.
- Does not submit applications to external company websites.
- Does not include user authentication.

Future enhancements:

- Live job vacancy integration.
- Student authentication.
- Resume analysis and job recommendations.
- Web-based placement dashboard.
- AI-powered interview evaluation.
- Integration with AI clients such as Claude Desktop.

## 12. Conclusion

PlaceMate demonstrates how the Model Context Protocol connects AI applications with backend services. Developing this project helped me understand MCP architecture, Python backend development, database integration, and structured communication through tools, resources, and prompts.

Project Type: MCP-Based AI Application

Language: Python

Database: SQLite

Development Environment: VS Code

Testing Tool: MCP Inspector