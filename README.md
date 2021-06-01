# Angular Travis CI

Application example using [Angular 12](https://angular.io/) and [Travis CI](https://www.travis-ci.com/) service.

Available in:

* [GitHub Pages](https://rodrigokamada.github.io/angular-travisci/)



[![Website](https://shields.braskam.com/v1/shields?name=website&format=rectangle&size=small)](https://rodrigo.kamada.com.br)
[![LinkedIn](https://shields.braskam.com/v1/shields?name=linkedin&format=rectangle&size=small)](https://www.linkedin.com/in/rodrigokamada)
[![Twitter](https://shields.braskam.com/v1/shields?name=twitter&format=rectangle&size=small&socialAccount=rodrigokamada)](https://twitter.com/rodrigokamada)



## Prerequisites


Before you start, you need to install and configure the tools:

* [git](https://git-scm.com/)
* [Node.js and npm](https://nodejs.org/)
* [Angular CLI](https://angular.io/cli)
* IDE (e.g. [Visual Studio Code](https://code.visualstudio.com/))



## Getting started


**1.** Create an application with the Angular base structure using the `@angular/cli` com with the route file and the SCSS style format.

```shell
ng new angular-travisci
? Would you like to add Angular routing? Yes
? Which stylesheet format would you like to use? SCSS   [ https://sass-lang.com/documentation/syntax#scss                ]
CREATE angular-travisci/README.md (1061 bytes)
CREATE angular-travisci/.editorconfig (274 bytes)
CREATE angular-travisci/.gitignore (604 bytes)
CREATE angular-travisci/angular.json (3267 bytes)
CREATE angular-travisci/package.json (1078 bytes)
CREATE angular-travisci/tsconfig.json (783 bytes)
CREATE angular-travisci/.browserslistrc (703 bytes)
CREATE angular-travisci/karma.conf.js (1433 bytes)
CREATE angular-travisci/tsconfig.app.json (287 bytes)
CREATE angular-travisci/tsconfig.spec.json (333 bytes)
CREATE angular-travisci/src/favicon.ico (948 bytes)
CREATE angular-travisci/src/index.html (301 bytes)
CREATE angular-travisci/src/main.ts (372 bytes)
CREATE angular-travisci/src/polyfills.ts (2820 bytes)
CREATE angular-travisci/src/styles.scss (80 bytes)
CREATE angular-travisci/src/test.ts (743 bytes)
CREATE angular-travisci/src/assets/.gitkeep (0 bytes)
CREATE angular-travisci/src/environments/environment.prod.ts (51 bytes)
CREATE angular-travisci/src/environments/environment.ts (658 bytes)
CREATE angular-travisci/src/app/app-routing.module.ts (245 bytes)
CREATE angular-travisci/src/app/app.module.ts (393 bytes)
CREATE angular-travisci/src/app/app.component.scss (0 bytes)
CREATE angular-travisci/src/app/app.component.html (23809 bytes)
CREATE angular-travisci/src/app/app.component.spec.ts (1087 bytes)
CREATE angular-travisci/src/app/app.component.ts (221 bytes)
✔ Packages installed successfully.
```

**2.** Create the `.travis.yml` file.

```shell
touch .travis.yml
```

**3.** Configure the `.travis.yml` file with the content below.

```yaml
notifications:
  email:
    recipients:
      - rodrigo@kamada.com.br

language: node_js

node_js:
  - 14

before_script:
  - npm install

script:
  - npm run test:headless

before_deploy:
  - npm run build:prod

deploy:
  provider: pages
  skip_cleanup: true
  github_token: $GITHUB_TOKEN
  local_dir: dist/angular-travisci
  on:
    branch: master
```

**4.** Change the `package.json` file and add the scripts below.

```json
  "build:prod": "ng build --prod --base-href https://rodrigokamada.github.io/angular-travisci/",
  "test:headless": "ng test --watch=false --browsers=ChromeHeadless"
```

**5.** Change the `src/app/app.component.spec.ts` file and remove the tests `should have as title 'angular-travisci'` and `should render title`.

**6.** Run the test with the command:

```shell
npm run test:headless
```

**6.** Run the application with the command:

```shell
npm start
```

**6.** Create the account on the GitHub.

**6.1.** Access the site [https://github.com/](https://github.com/) and click on the button *Sign up*.

![GitHub Initial page](docs/images/github-step1.png)

**6.2.** Fill in the fields *Username*, *Email address*, *Password*, click on the button *Verify* to solve the puzzle and click on the button *Create account*.

![GitHub Sign up](docs/images/github-step2.png)

**6.3.** Click on the menu with the avatar and click on the menu *Settings*.

![GitHub Menu avatar](docs/images/github-step3.png)

**6.4.** Click on the menu *Developer settings*.

![GitHub Settings](docs/images/github-step4.png)

**6.5.** Click on the menu *Personal access tokens*.

![GitHub Developer settings](docs/images/github-step5.png)

**6.6.** Click on the button *Generate new token*.

![GitHub Personal access tokens](docs/images/github-step6.png)

**6.7.** Fill in the field *Note*, select the option *repo* and click on the button *Create token*.

![GitHub Generate new token](docs/images/github-step7.png)

**6.8.** Copy the generated token, which in my case is *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*.
Copy the generated token and in my case the token 123345345 was generated because it will be used in Travis CI.

![GitHub Create token](docs/images/github-step8.png)

**7.** Create the account on the Travis CI.

**7.1.** Access the site [https://travis-ci.com/](https://travis-ci.com/) and click on the button *Sign up*.

![Travis CI Initial page](docs/images/travisci-step1.png)

**7.2.** Click on the button *SIGN IN WITH GITHUB* to sign in with GitHub account.

![Travis CI Sign up](docs/images/travisci-step2.png)

**7.3.** If Travis CI requests permission to list the repositories, accept the permission. Click on the repository link *angular-travisci*.

![Travis CI List repositories](docs/images/travisci-step3.png)

**7.4.** Click on the menu *More options* and click on the menu *Settings*.

![Travis CI Repository](docs/images/travisci-step4.png)

**7.5.** Fill in the fields *NAME* with the value *GITHUB_TOKEN*, *VALUE* with the value of your token generated on GitHub and click on the button *Add*.

![Travis Settings](docs/images/travisci-step5.png)
