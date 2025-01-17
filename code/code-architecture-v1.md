## Overview

- `apps` - top level applications, combine features and services, are deployable
  - `/api`
  - `/web`
- `features` - business logic services, used by applications
  - `/feature-1`
  - `/feature-2`
- `config` - configurations, used by features, database, shared services
- `database` - database schemas, migrations, used in features
- `shared` - shared services, utils, used in other features
  - `/services`
  - `/utils`

## Dependency Rules

- `apps/*` -> `features/*`, `config/*`, `shared/*`
- `features/*` -> `database`, `config/*`, `shared/*`
- `database` -> `config/*`
- `shared/services/*` -> `config/*`, `shared/utils/*`
