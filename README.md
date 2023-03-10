<h1 align="center">
  <a href="https://github.com/near/boilerplate-template">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/near/boilerplate-template/main/docs/images/pagoda_logo_light.png">
      <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/near/boilerplate-template/main/docs/images/pagoda_logo_dark.png">
      <img alt="" src="https://raw.githubusercontent.com/near/boilerplate-template/main/docs/images/pagoda_logo_dark.png">
    </picture>
  </a>
</h1>

<div align="center">
  Boilerplate Template React
  <br />
  <br />
  <a href="https://github.com/near/boilerplate-template/issues/new?assignees=&labels=bug&template=01_BUG_REPORT.md&title=bug%3A+">Report a Bug</a>
  ·
  <a href="https://github.com/near/boilerplate-template/issues/new?assignees=&labels=enhancement&template=02_FEATURE_REQUEST.md&title=feat%3A+">Request a Feature</a>
  .
  <a href="https://github.com/near/boilerplate-template/issues/new?assignees=&labels=question&template=04_SUPPORT_QUESTION.md&title=support%3A+">Ask a Question</a>
</div>

<div align="center">
<br />

[![Pull Requests welcome](https://img.shields.io/badge/PRs-welcome-ff69b4.svg?style=flat-square)](https://github.com/near/boilerplate-template/issues?q=is%3Aissue+is%3Aopen+label%3A%22help+wanted%22)
[![code with love by near](https://img.shields.io/badge/%3C%2F%3E%20with%20%E2%99%A5%20by-near-ff1414.svg?style=flat-square)](https://github.com/near)

</div>

<details open="open">
<summary>Table of Contents</summary>

- [Getting Started](#getting-started)
    - [Prerequisites](#prerequisites)
    - [Installation](#installation)
- [Usage](#usage)
- [Exploring The Code](#exploring-the-code)
- [Deploy](#deploy)
  - [Step 0: Install near-cli (optional)](#step-0-install-near-cli-optional)
  - [Step 1: Create an account for the contract](#step-1-create-an-account-for-the-contract)
  - [Step 2: deploy the contract](#step-2-deploy-the-contract)
  - [Step 3: set contract name in your frontend code](#step-3-set-contract-name-in-your-frontend-code)
- [Troubleshooting](#troubleshooting)
  - [Deploy on Vercel](#deploy-on-vercel)
  - [Roadmap](#roadmap)
  - [Support](#support)
  - [Project assistance](#project-assistance)
  - [Contributing](#contributing)
  - [Authors \& contributors](#authors--contributors)
  - [Security](#security)

</details>

---

## About

This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app) and [`tailwindcss`](https://tailwindcss.com/docs/guides/nextjs) created for easy-to-start as a React skeleton template in the Pagoda Gallery. Smart-contract was initialized with [create-near-app]. Use this template and start to build your own gallery project!

### Built With

[`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app), [`tailwindcss`](https://tailwindcss.com/docs/guides/nextjs), [`tailwindui`](https://tailwindui.com/), [`@headlessui/react`](https://headlessui.com/), [`@heroicons/react`](https://heroicons.com/), [create-near-app], [`amazing-github-template`](https://github.com/dec0dOS/amazing-github-template)

Getting Started
==================

### Prerequisites

Make sure you have a [current version of Node.js](https://nodejs.org/en/about/releases/) installed – we are targeting versions `18>`.

Read about other [prerequisites](https://docs.near.org/develop/prerequisites) in our docs.

### Installation


Install all dependencies:

    npm install


Build your contract:

    npm run build

Deploy your contract to TestNet with a temporary dev account:

    npm run deploy


Usage
=====

Start your frontend in development mode:

    npm run dev

Start your frontend in production mode:

    npm run start

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

Test your contract:

    npm run test

Exploring The Code
==================

1. The smart-contract code lives in the `/contract` folder. See the README there for
   more info. In blockchain apps the smart contract is the "backend" of your app.
2. The frontend code lives in the `/frontend` folder. You can start editing the page by
   modifying `frontend/pages/index.tsx`. The page auto-updates as you edit the file.
   This is your entrypoint to learn how the frontend connects to the NEAR blockchain.
3. Test your contract (must use node v16): `npm test`, this will run the tests in `integration-tests` directory.
4. [API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `frontend/pages/api/hello.ts`.
5. The `frontend/pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.
6. This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.


Deploy
======

Every smart contract in NEAR has its [own associated account][NEAR accounts].
When you run `npm run deploy`, your smart contract gets deployed to the live NEAR TestNet with a temporary dev account.
When you're ready to make it permanent, here's how:


Step 0: Install near-cli (optional)
-------------------------------------

[near-cli] is a command line interface (CLI) for interacting with the NEAR blockchain. It was installed to the local `node_modules` folder when you ran `npm install`, but for best ergonomics you may want to install it globally:

    npm install --global near-cli

Or, if you'd rather use the locally-installed version, you can prefix all `near` commands with `npx`

Ensure that it's installed with `near --version` (or `npx near --version`)


Step 1: Create an account for the contract
------------------------------------------

Each account on NEAR can have at most one contract deployed to it. If you've already created an account such as `your-name.testnet`, you can deploy your contract to `near-blank-project.your-name.testnet`. Assuming you've already created an account on [NEAR Wallet], here's how to create `near-blank-project.your-name.testnet`:

1. Authorize NEAR CLI, following the commands it gives you:

      near login

2. Create a subaccount (replace `YOUR-NAME` below with your actual account name):

      near create-account near-blank-project.YOUR-NAME.testnet --masterAccount YOUR-NAME.testnet

Step 2: deploy the contract
---------------------------

Use the CLI to deploy the contract to TestNet with your account ID.
Replace `PATH_TO_WASM_FILE` with the `wasm` that was generated in `contract` build directory.

    near deploy --accountId near-blank-project.YOUR-NAME.testnet --wasmFile PATH_TO_WASM_FILE


Step 3: set contract name in your frontend code
-----------------------------------------------

Modify `NEXT_PUBLIC_CONTRACT_NAME` in `frontend/.env.local` that sets the account name of the contract. Set it to the account id you used above.

    NEXT_PUBLIC_CONTRACT_NAME=near-blank-project.YOUR-NAME.testnet


Troubleshooting
===============

On Windows, if you're seeing an error containing `EPERM` it may be related to spaces in your path. Please see [this issue](https://github.com/zkat/npx/issues/209) for more details.


  [create-next-app]: https://github.com/vercel/next.js/tree/canary/packages/create-next-app
  [Node.js]: https://nodejs.org/en/download/package-manager
  [tailwindcss]: https://tailwindcss.com/docs/guides/nextjs
  [create-near-app]: https://github.com/near/create-near-app
  [jest]: https://jestjs.io/
  [NEAR accounts]: https://docs.near.org/concepts/basics/account
  [NEAR Wallet]: https://wallet.testnet.near.org/
  [near-cli]: https://github.com/near/near-cli


You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.

## Roadmap

See the [open issues](https://github.com/near/boilerplate-template/issues) for a list of proposed features (and known issues).

- [Top Feature Requests](https://github.com/near/boilerplate-template/issues?q=label%3Aenhancement+is%3Aopen+sort%3Areactions-%2B1-desc) (Add your votes using the 👍 reaction)
- [Top Bugs](https://github.com/near/boilerplate-template/issues?q=is%3Aissue+is%3Aopen+label%3Abug+sort%3Areactions-%2B1-desc) (Add your votes using the 👍 reaction)
- [Newest Bugs](https://github.com/near/boilerplate-template/issues?q=is%3Aopen+is%3Aissue+label%3Abug)

## Support

Reach out to the maintainer:

- [GitHub issues](https://github.com/near/boilerplate-template/issues/new?assignees=&labels=question&template=04_SUPPORT_QUESTION.md&title=support%3A+)

## Project assistance

If you want to say **thank you** or/and support active development of Boilerplate Template React:

- Add a [GitHub Star](https://github.com/near/boilerplate-template) to the project.
- Tweet about the Boilerplate Template React.
- Write interesting articles about the project on [Dev.to](https://dev.to/), [Medium](https://medium.com/) or your personal blog.

Together, we can make Boilerplate Template React **better**!

## Contributing

First off, thanks for taking the time to contribute! Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make will benefit everybody else and are **greatly appreciated**.


Please read [our contribution guidelines](docs/CONTRIBUTING.md), and thank you for being involved!

## Authors & contributors

The original setup of this repository is by [Dmitriy Sheleg](https://github.com/shelegdmitriy).

For a full list of all authors and contributors, see [the contributors page](https://github.com/near/boilerplate-template/contributors).

## Security

Boilerplate Template React follows good practices of security, but 100% security cannot be assured.
Boilerplate Template React is provided **"as is"** without any **warranty**. Use at your own risk.

_For more information and to report security issues, please refer to our [security documentation](docs/SECURITY.md)._
