# Roadmap

## Phase 1, skeleton
- Init Go module
- Add Cobra, or simple stdlib subcommand parser
- Add SQLite migrations
- Add domain structs
- Add repo layer

## Phase 2, agent management
- Implement `add`, `config`, `list`
- Interactive prompts
- Unique slug validation
- Table output

## Phase 3, secrets + profiles
- Keychain integration
- Profile CRUD
- ENV resolution order:
    - base process env
    - profile vars
    - agent vars
    - CLI overrides

## Phase 4, spawning
- One harness only
- Persist Run row
- Track PID/session
- `list` shows busy/idle

## Phase 5, polish
- Good help text
- JSON output for scripting
- README
- install instructions
- tests

