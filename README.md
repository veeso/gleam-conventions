# Gleam Conventions

![claude](https://img.shields.io/badge/Claude-D97757?style=for-the-badge&logo=claude&logoColor=white)
![gleam](https://img.shields.io/badge/Gleam-ffaff3?style=for-the-badge&logo=gleam&logoColor=white)

A [Claude Code](https://claude.ai/code) skill that enforces idiomatic Gleam coding conventions when writing or modifying `.gleam` files. The skill is based on patterns observed across major Gleam projects (stdlib, gleam_otp, gleam_erlang, Lustre, mug, gftp) and the official Gleam documentation.

## What it does

When activated, the skill instructs Claude Code to follow the **Pragmatic Gleam Guidelines** (`gleam-guidelines.txt`) before writing or modifying any Gleam code. The guidelines cover:

- **Naming conventions** - `snake_case` for functions/variables, `PascalCase` for types/constructors, stdlib naming patterns
- **Module organization** - package structure, `internal/` for private APIs, focused modules
- **Documentation** - module docs (`////`), item docs (`///`), canonical sections, variant docs
- **Error handling** - `Result` types, specific error types, `describe_error`, `use` chaining
- **Type design** - opaque types, custom types, type aliases, labelled arguments
- **Import conventions** - qualified imports preferred, type-only imports, ordering
- **Pattern matching** - exhaustive matching, pattern-over-conditionals
- **Pipe operator** - subject-first parameter design for clean pipe chains
- **Testing** - mirror source structure, descriptive test names, `_test` suffix
- **Examples** - separate projects in `examples/` with path dependencies
- **OTP actors** - actor model, opaque messages, handle aliases, state guards, request-reply
- **Project config** - `gleam.toml`, `gleam format`, conventional commits
- **Library design** - wrap externals, callback resources, `with_*` configuration
- **FFI** - isolate in `_ffi.erl` / `_ffi.mjs` files

## Install

### Global install (all projects)

Clone the repository and copy the `gleam-conventions` directory into your global Claude Code skills directory:

```bash
git clone https://github.com/veeso/gleam-conventions.git
cp -r gleam-conventions/gleam-conventions ~/.claude/skills/gleam-conventions
```

This makes the skill available in every project you work on with Claude Code.

### Per-project install

Clone the repository and copy the `gleam-conventions` directory into your project's `.claude/skills/` directory:

```bash
git clone https://github.com/veeso/gleam-conventions.git
mkdir -p /path/to/your/project/.claude/skills
cp -r gleam-conventions/gleam-conventions /path/to/your/project/.claude/skills/gleam-conventions
```

This makes the skill available only within that specific project.

### Verify installation

After installing, start Claude Code and the skill should be listed when you run `/skills`. You can verify it's working by asking Claude to write a simple Gleam function - it should follow the guidelines automatically.

## Guidelines reference

The full guidelines are in [`gleam-conventions/gleam-guidelines.txt`](./gleam-conventions/gleam-guidelines.txt). Each guideline has a unique ID (e.g., `G-CANONICAL-DOCS`) for easy reference. Here's the complete list:

| ID | Guideline |
| --- | --- |
| G-DESIGN-FOR-AI | Design with AI use in mind |
| G-SNAKE-CASE-FN | Use snake_case for functions and variables |
| G-PASCAL-CASE-TYPES | Use PascalCase for types and constructors |
| G-CONST-NAMES | Constants use lowercase snake_case |
| G-STDLIB-NAMES | Follow standard library naming patterns |
| G-MODULE-STRUCTURE | Modules mirror the package name |
| G-INTERNAL-MODULES | Internal modules are private implementation |
| G-FOCUSED-MODULES | Keep modules focused |
| G-MODULE-DOCS | Module documentation is mandatory |
| G-CANONICAL-DOCS | Public items have documentation comments |
| G-DOCUMENT-VARIANTS | Document type variants |
| G-RESULT-ERRORS | Use Result for fallible operations |
| G-ERROR-TYPES | Define situation-specific error types |
| G-RESULT-ALIAS | Provide Result type aliases |
| G-USE-RESULT-CHAIN | Use `use` for Result chaining |
| G-ASSERT-FOR-BUGS | Assertions are for programming bugs |
| G-OPAQUE-TYPES | Use opaque types for encapsulation |
| G-CUSTOM-TYPES | Use custom types idiomatically |
| G-TYPE-ALIASES | Use type aliases for clarity |
| G-LABELLED-ARGS | Use labelled arguments for clarity |
| G-QUALIFIED-IMPORTS | Prefer qualified imports |
| G-EXHAUSTIVE-MATCH | Exhaustive pattern matching |
| G-PATTERN-OVER-IF | Use pattern matching over conditionals |
| G-PIPE-FRIENDLY | Design functions for piping |
| G-TEST-STRUCTURE | Test files mirror source structure |
| G-TEST-NAMES | Test names describe behavior |
| G-EXAMPLES-AS-PROJECTS | Examples are separate projects |
| G-ACTOR-MODEL | Use the actor model for stateful services |
| G-ACTOR-MESSAGES-OPAQUE | Actor message types are opaque |
| G-ACTOR-HANDLE | Actor handle type alias |
| G-ACTOR-STATE-GUARDS | Actors serialize operations with state guards |
| G-ACTOR-REQUEST-REPLY | Use subjects for request-reply |
| G-GLEAM-TOML | gleam.toml conventions |
| G-FORMAT-CODE | Format code before committing |
| G-CONVENTIONAL-COMMITS | Use conventional commits |
| G-WRAP-EXTERNALS | Wrap external dependencies |
| G-CALLBACK-RESOURCES | Use callbacks for resource-scoped operations |
| G-CONFIG-WITH | Configuration via with_* functions |
| G-FFI-ISOLATION | Isolate FFI in dedicated files |
| G-IMMUTABLE-DATA | Prefer immutable data transformations |
| G-OPTION-NOT-NIL | Use Option for optional values |
| G-TODO-PANIC | Use todo and panic appropriately |

## License

This project is licensed under the MIT LICENSE. Read the full [LICENSE](./LICENSE).
