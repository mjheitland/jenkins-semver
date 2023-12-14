# Jenkins Multibranch Pipeline using Semantic Versioning with Conditional Commits

Jenkins [Git Changelog Plugin](https://plugins.jenkins.io/git-changelog/) helps to bump version in dependency of the commit message

Examples of commit messages: 
- "doc: improve documentation": 1.2.0 → 1.2.0 (no version bump)
- "chore: improve logging": 1.2.0 → 1.2.0 (no version bump)
- "fix: minor bug fix": 1.2.0 → 1.2.1 (increment in the patch version)
- "feat: add a new feature": 1.2.0 → 1.3.0 (increment in the minor version)
- "breaking: reimplement": 1.2.0 → 2.0.0 (increment in the major version)
