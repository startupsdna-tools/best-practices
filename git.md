# Git Best Practices

## Branch naming conventions

### Long-lived branches

- `main` - main branch, contains the latest stable version of the code;
- `dev`, `prod` - environment branches, contains the latest version of the code for that environment;

### Short-lived branches

- `feature/*` - branch for new feature development;
- `update/*` - branch for updates on existing feature or function;
- `bugfix/*` - branch for bug fixing;
- `hotfix/*` - branch for urgent bug fixing in released version;
- `refactor/*` - branch for code refactoring;
- `release/*` - branch for release preparation;

### Tags

- `v*.*` - tag for released version;

## Workflows

### Trunk-Based Workflow

Trunk-based workflow is a Git strategy where all developers work on a single branch, 
often called "trunk" or "main." Changes are small and integrated frequently.

Read more: [Trunk-Based Workflow](./git/trunkbased-workflow.md)

### Gitflow Workflow

The **Gitflow Workflow** is a popular branching model designed to facilitate the management of complex development processes,
particularly for projects involving versioned releases and active collaboration.

Read more: [Gitflow Workflow](./git/gitflow-workflow.md)
