# Steps to Create Vite React App with Jest and RTL

- create a folder for your project
- open in vscode
- run the following:

```js
npx degit fabri4c/vite-react-starter#main
```

- this will copy a repo from git that is a template project that includes different libraries including Jest and RTL
- `git init -b main`
- `npm i`
- create a new repo on GitHub, from the command line:

```js
gh repo create
```

- and follow the prompts
- `git remote add origin linkToGitHubRepo`
- `git add .`
- `git commit --m "message" --m "details"`
- `git push -u origin main`

- note: the `fabri4c/vite-react-starter#main` template is not set up to allow testing of jsx out of the box
  - it contains old packages - it is not updated and maintained
  - DO NOT USE
  - you can run `npm update --save` in your project's root to update all packages to the latest versions
    - note that this still won't magically set up testing of jsx in Jest

# React Testing Course for Beginners - Code and Test 3 Apps

## Github actions

- never used this before
- we click the Github actions tab in GH
- we scroll down to CI and choose 'building-and-testing-nodejs'
- we commit changes and this adds a yml file to our project
- yml contains config stuff
- examining the yml file, let's take a look at what some of it means

```js
on: push: branches: ['main'];
pull_request: branches: ['main'];
```

- this is saying our continuous integration (CI) should run on push and pull requests to the 'main' branch
- we'll run on ubuntu latest

```yml
runs-on: ubuntu-latest
```

- note - the .github folder has to be outside your project folder (i.e. at the same level as my-app in this case)
- further:
  - use `actions/checkout@v3` and `actions/setup-node@v3` and node 18.x instead of @v1

## Add Visual Testing

- at this point we've done two component tests
  - a url with the right text exists and the url is correct
  - a logo is rendered and the src is correct
- now we check that
  - the app renders correctly
  - app looks as expected on web and mobile
- for visual testing
  - webdriverio
  - visual snapshots in different resolutions in browser
    - makes sure its responsive and looks correct on different devices
- install webdriverio

```js
npm i @wdio/cli
```

- config

```js
npx wdio config
```

- options
  - E2E testing
  - In the cloud Sauce Labs
  - web app in the browser
  - chrome browser
  - sauce_username
  - sauce_access_key
  - eu
  - sauce connect - no (might be yes, not sure)
  - mocha
  - no compiler
  - webdriverio generate test files = no
  - add a plugin in to test setup = no (maybe?)
  - add a service to test setup = sauce and chromedriver
  - do let the configurator run npm (it will run pnpm and fail)
  - install the following:
  ```js
  npm add @wdio/local-runner@latest @wdio/mocha-framework@latest @wdio/spec-reporter@latest @wdio/sauce-service@latest --save-dev
  ```
  - `npm i @wdio/local-runner`
