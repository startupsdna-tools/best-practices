# Git Best Practices

## Branch naming conventions

### Long-lived branches

- `main` - main branch, contains the latest stable version of the code;
- `dev` - development branch, contains the latest development version of the code;

### Short-lived branches

- `feature/*` - branch for new feature development;
- `bugfix/*` - branch for bug fixing;
- `hotfix/*` - branch for urgent bug fixing in released version;
- `refactor/*` - branch for code refactoring;

### Tags

- `v*.*` - tag for released version;

## Workflows

### Simplified workflow

At early stages of a new product it makes sense to use Trunk-bases workflow.

- each merge request to main runs CI pipelines for linting and testing;
- each closed merge request or commits to main runs CD pipeline to build and deploy to testing server;

```mermaid
%%{init: { 'logLevel': 'debug', 'theme': 'base' } }%%
gitGraph
	commit
	commit
	branch feature/auth
	commit
	commit
	checkout main
	commit
	branch feature/todo-list
	commit
	commit
	checkout main
	merge feature/auth
	merge feature/todo-list
	branch bugfix/auth-error
	commit
	checkout main
	merge bugfix/auth-error tag: "v1.0"
```

### Development workflow

Used in order to separate development version from released version.

- each merge request to `dev` runs CI pipelines for linting and testing;
- each closed merge request or commits to `dev` runs CD pipeline to build and deploy to testing server;

```mermaid
%%{init: { 'logLevel': 'debug', 'theme': 'base' } }%%
gitGraph
	commit tag: "v1.0"
	branch dev
	commit
	branch feature/new-feature-1
	commit
	commit
	checkout dev
	commit
	branch feature/new-feature-2
	commit
	commit
	checkout dev
	merge feature/new-feature-1
	merge feature/new-feature-2
	checkout main
	merge dev tag: "v2.0"
```

### Hot-fix workflow

Used when it is required to make an urgent fix to a released version. 
After closing hotfix branch, it is merged back to main and dev branches.

```mermaid
%%{init: { 'logLevel': 'debug', 'theme': 'base' } }%%
gitGraph
    commit tag: "v1.0"
    checkout main
    branch hotfix/payment-error
    commit
    commit
    checkout main
    branch dev
    commit
    commit
    commit
    checkout main
    merge hotfix/payment-error tag: "v1.1"
    checkout dev
    merge hotfix/payment-error
    checkout dev
    commit
    commit
```