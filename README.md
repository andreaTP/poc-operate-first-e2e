
# Multitenant Apicurio Registry UI E2E - Operate First

This repository contains the User Interface End to End tests for the Operate First deployment of Apicurio Registry.

## Build & Run

 - [Typescript](https://www.typescriptlang.org/): language since it's the closer to the UI developers ecosystem
 - [NPM](https://www.npmjs.com/): build tool
 - [Node](https://nodejs.org/en/): runtime
 - [Playwright](https://playwright.dev/): framework for UI testing
 - [GH Action](https://docs.github.com/en/actions): infrastructure

To get started make sure you have an NPM and Node version that is compatible (npm `8.X`, node `16.X`) installed and available on the `PATH`.

```bash
npm install # Install all the needed Node dependencies
npx playwright install # Install all the Playwright dependencies and needed browsers
npx playwright test --project chromium # Executes the tests on a selected browser (`chromium` in this case)
```

if you need to debug something failing you can use the Playwright console and have a Playwright helper available in console by executing:

```bash
PWDEBUG=1 npx playwright test --project chromium --debug
```

### Setup

This repository uses GitHub Actions as infrastructure to run the tests agains publicly accessible services.
There are currently 2 CI running on the `main` branch:

 - `quick.yml` faster feedback loop
 - `full.yml` wide coverage of OSes/browsers

- `quick.yml`
run the tests only using the `chromium` browser on Linux

- `full.yml`
run the tests for full coverage including:

  - mac
  - linux
  - windows

and the browsers:

  - chromium
  - chrome
  - webkit
  - firefox
  - edge

The CI only runs on the `main` branch to avoid sharing secrets on branches and forks.

### Security

The only sensitive data in this project is the username and password used to login.
Those are stored in [GitHub Encrypted Secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets).
