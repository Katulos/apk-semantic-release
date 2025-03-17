# APK Semantic Release

[![GitHub Actions](https://github.com/Katulos/apk-semantic-release/actions/workflows/release.yml/badge.svg)](https://github.com/Katulos/apk-semantic-release/actions)  
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=Android&logoColor=white)
![release](https://github.com/Katulos/apk-semantic-release/actions/workflows/release.yml/badge.svg)
![develop](https://github.com/Katulos/apk-semantic-release/actions/workflows/develop.yml/badge.svg?branch=develop)

This project is a template for an Android application with an automated testing, building, and release process using `semantic-release`. The project includes an encrypted `keystore.jks.enc` for signing APKs and a GitHub Actions workflow for CI/CD.

## Features

- **Automatic Releases**: Uses `semantic-release` for automatic version management and releases.
- **Encrypted Keystore**: Includes an encrypted `keystore.jks.enc` for secure key storage.
- **CI/CD**: GitHub Actions workflow for automated testing, building, and publishing of APKs.
- **Semantic Versioning**: Automatic version management based on commit messages.

## Getting Started

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/Katulos/apk-semantic-release.git
   cd apk-semantic-release
   ```

2. Open the project in Android Studio.

3. Configure environment variables for decrypting `keystore.jks.enc` and signing the APK.

   Depending on the deployment environment (local or GitHub), configure the following variables:

    - **For Local Deployment**:
      Create a `keystore.properties` file in the root of the project and add the following lines:

      ```properties
      KEYSTORE_DECRYPTION_KEY=my_secret_key_12
      RELEASE_KEYSTORE_PASSWORD=123456
      RELEASE_KEY_PASSWORD=123456
      RELEASE_KEY_ALIAS=apk-semantic-release
      ```

      These are the default values. You can change them to your own.

    - **For GitHub Deployment**:
      Add the following secrets in the repository settings (GitHub Secrets):

        - `KEYSTORE_DECRYPTION_KEY`: Key for decrypting `keystore.jks.enc` (default: `my_secret_key_12`).
        - `RELEASE_KEYSTORE_PASSWORD`: Keystore password (default: `123456`).
        - `RELEASE_KEY_PASSWORD`: Key password (default: `123456`).
        - `RELEASE_KEY_ALIAS`: Key alias (default: `apk-semantic-release`).

## CI/CD

The project uses GitHub Actions to automate CI/CD processes. The workflow includes the following steps:

- **Testing**: Runs unit tests and instrumented tests.
- **Build**: Builds the APK with signing.
- **Release**: Automates releases using `semantic-release`.

### CI/CD Setup

1. Ensure the following secrets are configured in the repository:

    - `KEYSTORE_DECRYPTION_KEY`: Key for decrypting `keystore.jks.enc` (default: `my_secret_key_12`).
    - `RELEASE_KEYSTORE_PASSWORD`: Keystore password (default: `123456`).
    - `RELEASE_KEY_PASSWORD`: Key password (default: `123456`).
    - `RELEASE_KEY_ALIAS`: Key alias (default: `apk-semantic-release`).
    - `SEMANTIC_RELEASE_TOKEN` (for automatic releases)

2. The workflow is automatically triggered on pushes to the `master` branch or when a pull request is created.

## Using semantic-release

`semantic-release` automatically determines the version based on commit messages and creates a release on GitHub. The following commit types are supported:

- `feat`: New feature (minor version bump).
- `fix`: Bug fix (patch version bump).
- `BREAKING CHANGE`: Critical changes (major version bump).

Example commit:

```bash
git commit -m "feat: add new feature"
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

If you have any questions or suggestions, please create an [issue](https://github.com/Katulos/apk-semantic-release/issues) or contact the author.
