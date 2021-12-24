# Polywrap Centralized CD (Using Fleek)
In this example repo, we've followed [Fleek's guide](https://docs.fleek.co/fleek-cli/github-actions/) on how to create a continuous deployment of your static-site using GitHub Actions.

The difference here though is that we're deploying a built polywrapper instead. This allows us to continuously deploy polywrap packages, making them readily available using DNS based domain, and still have the files pinned and availble via IPFS.

## Live Package
**https://dawn-leaf-2772.on.fleek.co/**

## Process Overview
1. Developer pushes to repo
2. GitHub [workflow](./.github/workflows/wrapper-cd.yaml) is triggered
3. [Wrapper](./wrapper) is built
4. Fleek's GitHub action is used to deploy to a pre-existing "site" on their platform, using the [.fleek.json](./.fleek.json) configuration file.
5. Upon Fleek's platform API receiving the request for deployment, it will upload and pin the files to its IPFS nodes, and update the site's domain to the latest IPFS hash.

## Primary Use-Cases
Rapid development, where you want to be able to test new polywrap packages without paying gas fees to update an ENS domain with a new IPFS hash.
