# teller-playground

<https://github.com/tellerops/teller>

Secrets management where you can choose secrets backend, and can use it straight as environment variables.

In this example, `vault` and `dotenv` is used as secret backend.

## Setup

```bash
brew tap spectralops/tap && brew install teller
docker compose -f docker-compose-vault.yaml up
```

## Usage

[full example](https://github.com/tellerops/teller/blob/master/.teller.example.yml)

Notes:

- `env_sync`: fetch all keys from secret uri
- `env`: need to specify explicit key and correspond secret uri

```bash
# init
teller new # follow the prompts

# show values
teller show

# show values in .env format
teller env

# populate env
eval "$(teller sh)"
```

with vault:

```bash
export VAULT_TOKEN="testtoken"
export VAULT_ADDR="http://127.0.0.1:8200"

teller env -c .teller.vault.yaml
```
