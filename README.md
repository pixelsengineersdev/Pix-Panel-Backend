# PixelsEngineersDev --- Freelancer--Client Project Management Platform

A project management platform designed for freelancers and small
development teams to organize client work, track project progress,
collaborate on deliverables, and manage estimates and invoices in one
place.

The planned product includes a web application and dedicated Android/iOS
applications, backed by a Spring Boot REST API and MySQL database.

> **Project status:** Planning / active development. Features below
> describe the intended scope; availability depends on implementation
> progress.

## Overview

PixelsEngineersDev aims to make freelance project delivery more
transparent and organized. Freelancers and small teams can manage work
internally while giving clients a focused portal to view shared
progress, review deliverables, and follow estimates or invoice status.

## Goals

-   Manage clients and projects from a single workspace.
-   Break projects into tasks, subtasks, and milestones.
-   Track progress, due dates, and recent activity.
-   Share files and deliverables with the right people.
-   Let clients comment on and review submitted work.
-   Prepare estimates and track invoices and payment status.
-   Provide consistent experiences across web and mobile.
-   Protect client information with role-based and resource-level access
    controls.

## Target Users

-   **Freelancers:** Manage clients, projects, deliverables, estimates,
    and invoices.
-   **Workspace owners:** Configure workspaces, invite team members, and
    manage access.
-   **Team members:** Work on assigned projects and tasks according to
    permissions.
-   **Clients and stakeholders:** View shared project information,
    discuss work, and review deliverables.
-   **Platform administrators:** Support and operate the platform
    through separately controlled administrative capabilities.

## Planned Features

### Core MVP Modules

1.  **Authentication and User Profiles** --- Registration, login,
    account verification, password recovery, profiles, and preferences.
2.  **Workspace and Team Management** --- Workspaces, member
    invitations, and role management.
3.  **Client Management** --- Client records, contacts, and portal
    access.
4.  **Project Management** --- Project setup, scope, dates, status, and
    team/client associations.
5.  **Task and Subtask Management** --- Assignment, priority, status,
    descriptions, and due dates.
6.  **Milestones and Timeline** --- Milestone dates, completion
    criteria, and status.
7.  **Progress Dashboard** --- Project summaries, overdue work,
    milestone progress, and recent activity.
8.  **Client Portal** --- Client-scoped views of shared projects and
    updates.
9.  **Deliverables and Approvals** --- Submit work for review, approve
    or request changes, and retain version history.
10. **Comments and Activity Feed** --- Contextual discussions and
    timestamped activity.
11. **Files and Documents** --- Upload, organize, and securely share
    project files.
12. **Notifications** --- Relevant in-app and email notifications.
13. **Estimates and Quotations** --- Line items, totals, and estimate
    review status.
14. **Invoices and Payment Tracking** --- Invoice records, due dates,
    and manual payment-status tracking.
15. **Security, Audit, and Administration** --- Authorization, audit
    events, and operational controls.
16. **Web and Mobile Experience** --- Web application and dedicated
    Android/iOS applications using the backend API.

### Potential Post-MVP Features

-   Advanced reporting and data exports.
-   Task dependencies and advanced timeline views.
-   Push notifications and configurable workflows.
-   Custom workspace branding.
-   Integrations with GitHub/GitLab, calendars, accounting tools, and
    payment providers.
-   Subscription billing for the platform.
-   AI-assisted summaries and workflow suggestions.

## Technology Stack

  -----------------------------------------------------------------------
  Layer                               Planned technology
  ----------------------------------- -----------------------------------
  Backend API                         Java with Spring Boot

  Database                            MySQL

  Web client                          To be finalized

  Android application                 Dedicated mobile app; framework to
                                      be finalized

  iOS application                     Dedicated mobile app; framework to
                                      be finalized

  API style                           REST

  Delivery                            CI/CD and separate development,
                                      staging, and production
                                      environments
  -----------------------------------------------------------------------

Confirm exact framework versions, frontend/mobile technologies,
authentication approach, file storage, and deployment infrastructure
before implementation. Update this section as decisions are finalized.

## Architecture Overview

The intended architecture separates client applications from backend
business logic:

``` text
Web Application ───────┐
                       │
Android Application ───┼──> Spring Boot REST API ───> MySQL
                       │              │
iOS Application ───────┘              ├──> Email / Notifications
                                      ├──> File Storage
                                      └──> Logging / Monitoring
```

This diagram is conceptual. External services and storage providers will
depend on implementation decisions.

### Design Principles

-   Keep business rules and authorization checks on the server.
-   Use the same API contracts across web and mobile clients.
-   Apply workspace and resource-level access checks to protected data.
-   Use database migrations to manage schema changes.
-   Validate inputs and handle errors consistently.
-   Add automated tests for business rules, permissions, and critical
    workflows.

## Suggested Repository Structure

If maintained as a monorepo, the following is a suggested starting
point. Adapt it to match the actual repository.

``` text
freelancer-client-management-platform/
├── backend/              # Spring Boot REST API
├── web/                  # Web application
├── mobile-android/       # Android application
├── mobile-ios/           # iOS application
├── docs/                 # Product requirements, API notes, architecture
├── infrastructure/       # Deployment and environment configuration
├── .gitignore
└── README.md
```

Do not create empty folders solely to match this example; keep the
structure aligned with the code that exists.

## Getting Started

### Prerequisites

Install the tools required by the components you intend to run:

-   Git
-   A supported JDK version compatible with the selected Spring Boot
    version
-   MySQL
-   Maven or the project's configured build tool
-   Node.js and the chosen package manager, if required by the web
    client
-   Android Studio and/or Xcode for native mobile development, as
    applicable

### Clone the Repository

``` bash
git clone <YOUR_REPOSITORY_URL>
cd freelancer-client-management-platform
```

Replace `<YOUR_REPOSITORY_URL>` with the actual repository URL.

### Run the Backend

For a Maven-based Spring Boot application, a typical local workflow is:

``` bash
cd backend
./mvnw spring-boot:run
```

On Windows, use `mvnw.cmd spring-boot:run` if the Maven wrapper is
present. Configure the database and required environment variables
before starting the application.

### Run the Clients

Follow the setup instructions in the relevant `web/`, `mobile-android/`,
or `mobile-ios/` directory once those applications and their
package/build configuration are present.

> **Note:** These are starter instructions. Update them with verified
> commands, ports, environment variables, and test procedures for the
> actual repository before publishing.

## Configuration

Keep credentials and environment-specific values outside source control.
A local environment file or deployment secret store may be used,
depending on the chosen setup.

Typical configuration values may include:

``` dotenv
# Illustrative names only; map them to the application's actual configuration.
DB_HOST=localhost
DB_PORT=3306
DB_NAME=freelancer_platform
DB_USERNAME=your_local_db_user
DB_PASSWORD=your_local_db_password
```

Do not commit real passwords, API keys, signing keys, access tokens, or
production connection strings. Use least-privilege database accounts and
separate credentials for each environment.

## Development Workflow

The project follows a Scrum-inspired Agile approach with proposed
two-week sprints.

1.  Prioritize the product backlog and define a clear sprint goal.
2.  Split features into small stories with acceptance criteria.
3.  Implement changes on a feature branch.
4.  Run relevant unit, integration, and UI tests.
5.  Open a pull request and request code review.
6.  Merge only after required checks pass.
7.  Demonstrate the working increment and use feedback to reprioritize
    the backlog.

### Definition of Done

-   Acceptance criteria are met.
-   Code has been reviewed.
-   Relevant automated tests pass.
-   Authorization and validation are enforced server-side.
-   Loading, empty, error, and success states are handled where
    applicable.
-   No secrets are exposed in code or logs.
-   Build and database migration checks pass.
-   Documentation is updated when needed.

## Security and Privacy

Security is a core requirement, particularly because projects may
contain confidential client files and commercial information.

-   Enforce authentication and server-side authorization on protected
    endpoints.
-   Ensure users can access only workspaces and resources they are
    permitted to see.
-   Keep internal notes and private files hidden from clients unless
    explicitly shared.
-   Validate uploads, restrict file size/type, and authorize file
    downloads.
-   Use secure, expiring account verification and password-reset flows.
-   Avoid logging passwords, tokens, or sensitive client content.
-   Validate financial totals and payment records on the server.
-   Maintain audit history for sensitive actions.
-   Use backups, monitoring, and a tested recovery process.

The MVP payment feature is intended to track invoice and payment status
manually unless payment processing is explicitly implemented later. Do
not represent a manual record as a completed payment gateway
transaction.

## Roadmap

The following sequence is indicative and should be adjusted based on
team capacity and backlog refinement.

  -----------------------------------------------------------------------
  Phase                               Focus
  ----------------------------------- -----------------------------------
  Sprint 0                            Requirements, architecture,
                                      permissions, design tokens,
                                      repositories, CI, and environments

  Sprints 1--2                        Authentication, profiles,
                                      verification, and password recovery

  Sprint 3                            Workspace and team management

  Sprint 4                            Client management

  Sprint 5                            Project management

  Sprint 6                            Tasks and subtasks

  Sprint 7                            Milestones and progress dashboard

  Sprint 8                            Client portal, deliverables, and
                                      approvals

  Sprint 9                            Comments, activity, and
                                      notifications

  Sprint 10                           Estimates, invoices, and manual
                                      payment tracking

  Sprints 11--12                      Mobile coverage,
                                      integration/regression testing,
                                      user acceptance, and launch
                                      readiness
  -----------------------------------------------------------------------

These sprint numbers are planning estimates, not a delivery commitment.
Validate the schedule using team capacity and observed throughput.

## Contributing

Contributions and improvements should follow the repository's agreed
engineering standards.

1.  Check the backlog or open an issue before starting substantial work.
2.  Keep pull requests focused and describe the reason for the change.
3.  Include tests for new business rules and bug fixes.
4.  Document API, schema, or configuration changes.
5.  Never include secrets or private client data in commits, issues, or
    screenshots.

Add a `CONTRIBUTING.md` with project-specific branch naming, commit
conventions, review requirements, and local test commands when these are
established.

## License

No license has been specified yet. Add a `LICENSE` file and update this
section once the project owner has chosen the license. Until then, do
not assume the code is open source or freely reusable.

------------------------------------------------------------------------

**Maintained by PixelsEngineersDev.**
