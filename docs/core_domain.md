# Architecture outline

## Core domain

### Agent
- id
- name
- slug
- description
- type
- created_at
- updated_at

### EnvVar
- id
- owner_type (agent or profile)
- owner_id
- key
- value or secret_ref
- is_secret

### Profile
- id
- name
- kind (hizal, later others)
- description

### Run
- id
- agent_id
- profile_id nullable
- harness
- state (started, running, exited, failed)
- pid
- cwd
- session_ref
- started_at
- ended_at
- last_error

## Don't store secret values in SQLite
- store metadata in SQLite
- store real secrets in OS keychain
- SQLite keeps `secret_ref`

## Busy/idle model
Do not store `busy` as truth.
- Truth is active Run row + live process check.
- `aint list` computes busy/idle from latest run state
- On startup, reconcile stale runs if process dead

## Layers
- `cmd/aint`, CLI entry
- `internal/cli`, commands, prompts
- `internal/domain`, structs + rules
- `internal/store`, SQLite repos
- `internal/secrets`, keychain adapter
- `internal/harness`, spawn adapters
- `internal/runtime`, process tracking
- `internal/app`, use cases

## Harness abstraction
Make harness pluggable early
- `spawn(agent, profile, harness, opts)`
- Adapter resolves env, command, cwd, args
- First harness can be simple, even just shell command template
- Later Add Codex, Claude Code, OpenCode, etc
