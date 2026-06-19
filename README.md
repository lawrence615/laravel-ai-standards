# Laravel AI Standards

This repository defines a consistent architecture for Laravel applications, optimized for AI-assisted development tools.

It ensures every project follows the same structure, including:

- Repository pattern with interfaces
- DTO-based data transfer
- Form Request validation
- API Resources for responses
- Centralized response handling
- Clean separation of concerns

## Architecture Overview

```
laravel-app/
├── app/
│   ├── Repositories/
│   ├── Interfaces/
│   ├── DTOs/
│   ├── Responses/
│   ├── Traits/
│   └── Http/
│
├── app/Providers/
│   └── RepositoryServiceProvider.php
│
├── routes/
├── database/
├── tests/
│
├── .ai/
│   ├── KNOWLEDGE.md
│   ├── README.md
│   └── RULES.md   (optional but useful)
│
├── composer.json
└── artisan
```

## How to Use This Repository

### Option 1: Clone into a new Laravel project (Recommended)

```bash
$ cd /path/to/your/laravel/project
$ git clone git@github.com:yourname/laravel-ai-standards.git .ai
```

### Option 2: Reference manually
Developers can copy relevant sections into their Laravel project under:
- `docs/architecture.md`
- `.ai/KNOWLEDGE.md`

### Option 3: As a starter template
This repository can be used as a base for Laravel projects where architecture consistency is required.

---

### ✔ You can also add a “Who is this for?”

```md id="use2"
## Who This Is For

- Laravel developers who prefer strict architecture
- Teams using AI-assisted development tools
- Projects requiring consistency across multiple codebases
```

Then instruct your AI assistant:
```quote
Read .ai/knowledge.md and follow all defined architecture rules.
```
