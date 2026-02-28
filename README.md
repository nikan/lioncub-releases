# Lioncub

Lioncub is a VS Code extension for chatting with Mistral models through the native VS Code Chat UI.

## What It Does

Lioncub currently supports:
- native VS Code chat participant registration as `@mistral`
- secure Mistral API key storage in VS Code `SecretStorage`
- configurable model, temperature, token limit, and optional system prompt
- streaming responses in the chat UI
- connection testing and operational logs through a Lioncub output channel

## Install

Download the latest `.vsix` package from the [Releases page](https://github.com/nikan/lioncub-releases/releases).

Install it with:

```bash
code --install-extension lioncub-<version>.vsix
```

You can also install the `.vsix` from the VS Code Extensions view if you prefer a UI flow.

## Setup

1. Install the extension.
2. Run `Lioncub: Set API Key`.
3. Run `Lioncub: Test Connection`.
4. Open the VS Code Chat view and select `@mistral`.

## First Chat

1. Run `Lioncub: Set API Key`.
2. Run `Lioncub: Test Connection`.
3. Open chat and address `@mistral`.
4. Submit a prompt.
5. If something fails, run `Lioncub: Show Logs` and inspect the `Lioncub` output channel.

## Available Commands

- `Lioncub: Set API Key`
- `Lioncub: Clear API Key`
- `Lioncub: Test Connection`
- `Lioncub: Show Status`
- `Lioncub: Show Logs`

## Settings

Lioncub contributes these settings:

- `lioncub.defaultModel`
  Default Mistral model used for chat requests.
- `lioncub.availableModels`
  Allowlist of model IDs the extension accepts.
- `lioncub.temperature`
  Sampling temperature from `0` to `2`.
- `lioncub.maxTokens`
  Maximum requested response tokens.
- `lioncub.systemPrompt`
  Optional base system instruction.
- `lioncub.logLevel`
  One of `debug`, `info`, `warn`, `error`.

## Troubleshooting

### Missing or Invalid API Key

Symptoms:
- `Test Connection` fails
- chat shows an authentication error

Remedy:
- run `Lioncub: Set API Key`
- rerun `Lioncub: Test Connection`
- open `Lioncub: Show Logs` if the failure persists

### Invalid or Unavailable Model

Symptoms:
- chat fails before or during completion
- connection or request errors mention model availability

Remedy:
- check `lioncub.defaultModel`
- confirm the model exists in `lioncub.availableModels`
- keep `lioncub.defaultModel` inside the allowlist

### Network Failure

Symptoms:
- chat cannot reach Mistral
- connection test fails intermittently

Remedy:
- verify network connectivity from VS Code
- retry the request
- inspect `Lioncub: Show Logs` for the request lifecycle and error code

### Invalid Configuration

Symptoms:
- status or chat requests fail immediately
- errors mention Lioncub configuration

Remedy:
- open VS Code settings for `Lioncub`
- correct `defaultModel`, `availableModels`, `temperature`, `maxTokens`, or `logLevel`

## Logs

Lioncub writes operational logs to the `Lioncub` output channel.

The logs include:
- request start and completion
- model and session correlation
- durations and error codes

The logs intentionally do not include:
- API keys
- auth headers
- full prompt bodies
