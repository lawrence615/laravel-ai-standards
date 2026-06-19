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
$ git clone https://github.com/lawrence615/laravel-ai-standards.git .ai
```

Then add `.ai/` to your project’s `.gitignore` so the cloned directory is not committed into your main repository:

```bash
echo ".ai/" >> .gitignore
```

Note: Some IDEs may take a moment to detect the new `.ai` directory. If it does not appear immediately, refresh the project explorer or wait for the IDE’s file index to update.

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
