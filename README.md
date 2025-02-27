## Use `.NET NSec library for C#` based on [libsodium](https://libsodium.org/) to update repository secrets

### Repository Secret Update Workflow

This is a GitHub Actions workflow that updates a repository secret using [NSec .NET for C#](https://github.com/ektrah/nsec). 

Proof-of-concept to update a secret using `NSec` rather than [Sodium.Core](https://github.com/ektrah/libsodium-core) as it is no longer maintained, and a possible candidate for a replacement for GitHub's [current recommendation](https://docs.github.com/en/rest/guides/encrypting-secrets-for-the-rest-api?apiVersion=2022-11-28#example-encrypting-a-secret-using-c).


The workflow performs the following tasks:
- Hashes an input message with BLAKE2b using NSec.Cryptography.
- Updates a specified repository secret with the generated hash.

## How to Use

1. Trigger the workflow manually.
2. Provide the following inputs:
   - **secret:** The new or updated Secret
   - **pat_token:** A Personal Access Token with repo permissions.
   - **secret_name:** The name of the repository secret to update.
