# Global Rules and Best Practices

## 1. General Principles
- Maintain **code integrity, stability, and security** across all projects.
- Enforce **minimal and necessary modifications** to prevent codebase disruptions.
- Ensure **all changes are reviewed, tested, and approved** before merging.
- Keep **documentation up to date** to align with codebase modifications.

## 2. Code Standards & Best Practices
- **Language Compliance:** Follow industry-standard guidelines for each programming language.
- **Linting & Formatting:** Use automated tools like ESLint, Prettier, Black, or Pylint.
- **Code Documentation:**
  - Every function, class, and module must include proper docstrings or comments.
  - Maintain structured documentation (`README.md`, API references, architecture diagrams, etc.).
  - Include inline documentation for non-trivial logic.
- **Naming Conventions:**
  - Use consistent naming (camelCase, PascalCase, or snake_case as per project guidelines).
  - Avoid abbreviations unless they are widely recognized.

## 3. Version Control & Branching Strategy
- Use **Git** for all version control operations.
- Follow **GitFlow** or a similar structured branching model:
  - `main` - Stable production-ready code.
  - `develop` - Latest development code, integrates all feature branches.
  - `feature/{name}` - Isolated development of new features.
  - `bugfix/{name}` - Isolated fixes for issues discovered during testing.
  - `hotfix/{name}` - Urgent production bug fixes.
  - `release/{version}` - Final refinements before merging to `main`.

### Commit Message Guidelines
Follow a structured commit message format:
```plaintext
type(scope): description
```
**Examples:**
```plaintext
feat(auth): implement JWT authentication
fix(ui): resolve navbar alignment issue on mobile
```
- **Type** (feat, fix, chore, docs, style, refactor, test, perf, build, ci, revert).
- **Scope** (module or feature affected).
- **Description** (concise summary of changes).

## 4. Pull Request & Review Workflow
- All code changes must go through a **Pull Request (PR)**.
- PRs should include:
  - A **detailed description** of changes.
  - **References to related issues**.
  - **Relevant test cases** and expected outcomes.
- No direct commits to `main` or `develop`.
- Use **Squash and Merge** for feature branches.
- Assign at least **one reviewer** before merging.

## 5. Security & Compliance
- **Authentication & Authorization:**
  - Use **OAuth2, JWT, or session-based authentication** where applicable.
  - Implement **role-based access control (RBAC)**.
- **Data Protection:**
  - Encrypt sensitive data (AES-256 for storage, TLS 1.3 for transit).
  - Enforce **secure coding practices** to mitigate vulnerabilities.
  - Regular security audits and compliance checks (GDPR, HIPAA, etc.).
- **Dependency Management:**
  - Audit third-party dependencies regularly.
  - Use tools like **Dependabot, Snyk, or OWASP Dependency-Check**.
  - Remove unused and outdated dependencies.

## 6. Testing & QA Standards
- **Unit Tests:** Required for all new functionality.
- **Integration & Functional Tests:** Validate end-to-end workflows.
- **Code Coverage:** Maintain at least **80%+ coverage**.
- **Automated Testing:** Enforce testing via CI/CD pipelines.
- **Security Testing:** Regularly perform static analysis and penetration testing.

## 7. CI/CD & Deployment Guidelines
- Use automated **CI/CD pipelines** for:
  - Linting and static code analysis.
  - Running tests (unit, integration, regression).
  - Building and packaging artifacts.
  - Deploying to staging and production environments.
- Define rollback mechanisms for **failed deployments**.
- Maintain **observability** with logs and monitoring tools (e.g., Prometheus, Grafana, Sentry).

## 8. Communication & Documentation
- Use **issue tracking tools** (Jira, GitHub Issues, etc.) for project tracking.
- Maintain structured **API documentation** using OpenAPI or Swagger.
- Follow **standardized meeting and reporting structures** for team updates.
- Enforce **knowledge sharing** through design documents and documentation updates.

## 9. Prohibited Actions
- **No direct commits** to protected branches (`main`, `develop`).
- **No use of deprecated APIs, insecure libraries, or unauthorized third-party tools**.
- **No exposure of sensitive credentials** in logs, commits, or PRs.
- **No hardcoded secrets or tokens**—use environment variables instead.

## 10. Continuous Improvement
- Conduct **regular code reviews and retrospectives**.
- Encourage **feedback and process enhancements**.
- Stay updated with **industry best practices and evolving standards**.
- Foster a **culture of collaboration and learning** within the team.

