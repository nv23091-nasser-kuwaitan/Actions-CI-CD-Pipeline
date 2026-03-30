# GitHub Actions CI/CD – Submission Write-Up

## End-to-End Flow (Part C)

A small change (a comment fix) was pushed to the `dev` branch, which automatically triggered the CI workflow. The workflow checked out the code, set up Python 3.11, installed all dependencies, ran flake8 for linting, and executed the pytest test suite — all passing with a green check. A Pull Request was then opened from `dev` into `main` and merged after CI passed. Finally, a new GitHub Release (`v0.3.0`) was published with release notes describing the changes. This triggered the CD workflow, which built the Docker image and pushed it to DockerHub tagged as both `0.3.0` and `latest`, confirming the full pipeline worked end to end.

---

## Reflection: What I Learned About GitHub Actions and Automation

Working through this assignment made it clear how much manual effort CI/CD pipelines eliminate. Before adding GitHub Actions, every test run, lint check, and Docker build had to be done manually — easy to skip or forget. By defining the workflows in YAML files committed to the repository, every push and pull request is automatically validated, which catches mistakes early before they reach production. The CD workflow especially highlighted the value of automation: publishing a release with a version tag is enough to trigger a full Docker build and push to the registry without any manual commands. I also learned how GitHub Secrets work to keep credentials out of source code, which is essential for security. Overall, the biggest takeaway is that automation makes the development process more reliable and consistent — the pipeline does the same checks every single time, with no human error.
