> [!CAUTION]
> Proof-of-Concept
> Read more here for insight: [libsodium investigation:](https://github.com/appatalks/gh_nsec_secrets_update/issues/1)

## Use Libsodium directly with `P/Invoke` method to Encrypt and update GitHub Repository Secret 

### Repository Secret Update Workflow

This is a GitHub Actions workflow that updates a repository secret using C# and .NET bindings.

Proof-of-concept to update a secret using `libsodium` rather than [Sodium.Core](https://github.com/ektrah/libsodium-core) as it is no longer maintained, and a possible candidate for a replacement to GitHub's [current recommendation](https://docs.github.com/en/rest/guides/encrypting-secrets-for-the-rest-api?apiVersion=2022-11-28#example-encrypting-a-secret-using-c).

> [!NOTE]
> - *`P/Invoke` with Libsodium*: The project uses [P/Invoke to call native Libsodium functions](https://learn.microsoft.com/en-us/dotnet/standard/native-interop/pinvoke) (`sodium_init` and `crypto_box_seal`) from C#.
> - *Sealed Box Encryption*: The `crypto_box_seal` method encrypts data using the recipient's public key without needing a sender key pair.

## How to Use

0. Use this Actions Workflow: [libsodium-dev-secret-update.yml](https://github.com/appatalks/gh_nsec_secrets_update/blob/main/libsodium-dev-secret-update.yml)
   - It's not polished so you will need to look at the code to set up your variables, etc.
2. Trigger the workflow manually.
3. Provide the following inputs:
   - **secret:** The new or updated Secret
   - **pat_token:** A Personal Access Token with repo permissions.
   - **secret_name:** The name of the repository secret to update.
