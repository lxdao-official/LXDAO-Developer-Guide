# LXDAO Develop Guide

This document introduces the tech stacks, branch styles, development workflow, and code styles in LXDAO.

## Tech stacks

Try to use as simple as possible tech stacks to finish the project, DO NOT introduce unnecessary tools, libraries, etc.

### Languages

- JavaScript / TypeScript for full stack developments
- Python for crawlers or scripts
- Solidity for smart contracts
- Others for specific projects

### FrontEnd

- React.js Ecosystem
- [MUI](https://mui.com/) for UI components
- Next.js

### BackEnd

- Nest.js for APIs
- Redis for cache
- PostgreSQL

### SaaS and Cloud Services

- [Vercel](https://vercel.com/) for FrontEnd projects and simple FaaS logic requirements
- [Heroku](https://www.heroku.com/) for simple BackEnd APIs
- AWS AKS for complex BackEnd applications
- AWS Lightsail for DEV environment

### Others

- Prettier for code format
- GitHub Actions for CICD
- VSCode

## Development

### Environment

- `Local` your local machine
- `DEV` remote testing and preview environment
- `SIT` only for big projects, for on-production verification
- `Production` production environment for users

`Local`, `DEV`, and `Production` are required environments, `SIT` just for big projects.

### Branch styles

- `main` for `Production` environment, the code in this branch reflects the latest production application, protected by default
- `develop` for `DEV` or `SIT` environment, latest version of code
- `feature/[feature-name]` for specific changes

### Development workflow

- Create or get a ticket on the Project Management tool ([ClickUp](https://clickup.com/))
- Checkout a branch from `develop` for the change, the branch name should follow the pattern `feature/[feature-name]`
- Coding on your local machine
- Submit a PR to the `develop` branch, verify and test on the `DEV` environment
- Submit a PR from `develop` to `main`, ask someone to do code review and approve your PR
- After merging into `main`, will deploy your code to production

## Code Styles

We use [Prettier](https://prettier.io/) for code formatting. Please install the Prettier plugin and create the following configuration in your project:

```
{
  "singleQuote": true,
  "trailingComma": "all"
}
```

TODO add more details

## Music when coding 😁

- [The Midnight](https://www.youtube.com/channel/UC-sM_PLqzgktdUcW2LEKKkQ)

## References

- [How to contribute React](https://reactjs.org/docs/how-to-contribute.html)
- [Airbnb JavaScript Style Guide](https://airbnb.io/javascript/react/)
