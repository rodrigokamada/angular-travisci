# Angular Travis CI


Application example built with [Angular 13](https://angular.io/) and hosted on [GitHub Pages](https://pages.github.com/) using [Travis CI](https://www.travis-ci.com/).

This tutorial was posted on my [blog](https://rodrigo.kamada.com.br/blog/hospedando-uma-aplicacao-angular-no-github-pages-usando-o-travis-ci) in portuguese and on the [DEV Community](https://dev.to/rodrigokamada/hosting-an-angular-application-on-github-pages-using-travis-ci-5dip) in english.

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


### Create and configure the account on the GitHub


**1.** Let's create the account. Access the site [https://github.com/](https://github.com/) and click on the button *Sign up*.

![GitHub - Initial page](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722987/Blog/angular-travisci/github-step1.png)

**2.** Fill in the fields *Username*, *Email address*, *Password*, click on the button *Verify* to solve the challenge and click on the button *Create account*.

![GitHub - Sign up](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722986/Blog/angular-travisci/github-step2.png)

**3.** Let's generate the token that will be used in Travis CI. Click on the menu with the avatar and click on the menu *Settings*.

![GitHub - Menu Settings](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722986/Blog/angular-travisci/github-step3.png)

**4.** Click on the menu *Developer settings*.

![GitHub - Settings](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722986/Blog/angular-travisci/github-step4.png)

**5.** Click on the menu *Personal access tokens*.

![GitHub - Developer settings](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722986/Blog/angular-travisci/github-step5.png)

**6.** Click on the button *Generate new token*.

![GitHub - Personal access tokens](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722986/Blog/angular-travisci/github-step6.png)

**7.** Fill in the field *Note*, select the option *repo* and click on the button *Create token*.

![GitHub - Generate new token](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722987/Blog/angular-travisci/github-step7.png)

**8.** Copy the generated token and, in my case, the `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` token was generated because this token will be configured in Travis CI.

![GitHub - Create token](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722987/Blog/angular-travisci/github-step8.png)

**9.** Let's create the repository. Click on the menu with the avatar and click on the menu *Your repositories*.

![GitHub - Menu Your repositories](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722987/Blog/angular-travisci/github-step9.png)

**10.** Click on the button *New*.

![GitHub - New repository](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722987/Blog/angular-travisci/github-step10.png)

**11.** Fill in the field *Repository bane* and click on the button *Create repository*.

![GitHub - Create repository](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722987/Blog/angular-travisci/github-step11.png)

**12.** Ready! Account created, token generated and repository [`https://github.com/rodrigokamada/angular-travisci`](https://github.com/rodrigokamada/angular-travisci) created.

![GitHub - Repository created](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722988/Blog/angular-travisci/github-step12.png)


### Create and configure the account on the Travis CI


**1.** Let's create the account. Access the site [https://travis-ci.com/](https://travis-ci.com/) and click on the button *Sign up*.

![Travis CI - Initial page](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722988/Blog/angular-travisci/travisci-step1.png)

**2.** Click on the button *SIGN IN WITH GITHUB* to sign in with GitHub account.

![Travis CI - Sign up](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722988/Blog/angular-travisci/travisci-step2.png)

**3.** If Travis CI requests permission to list the GitHub repositories, accept the request. Click on the repository link *angular-travisci*.

![Travis CI - List repositories](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722988/Blog/angular-travisci/travisci-step3.png)

**4.** Let's set up the GitHub access token. Click on the menu *More options* and click on the menu *Settings*.

![Travis CI - Repository](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722988/Blog/angular-travisci/travisci-step4.png)

**5.** Fill in the fields *NAME* with the value *GITHUB_TOKEN*, *VALUE* with the value of your token generated on GitHub and click on the button *Add*.

![Travis CI - Settings](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722988/Blog/angular-travisci/travisci-step5.png)

**6.** Ready! Account created and repository configured.

![Travis CI - Repository configured](https://res.cloudinary.com/rodrigokamada/image/upload/v1636722989/Blog/angular-travisci/travisci-step6.png)


### Create the Angular application


**1.** Let's create the application with the Angular base structure using the `@angular/cli` with the route file and the SCSS style format.

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
  - 16

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

**4.** Change the `package.json` file and add the scripts below. Replace the `rodrigokamada` value with your GitHub username.

```json
  "build:prod": "ng build --prod --base-href https://rodrigokamada.github.io/angular-travisci/",
  "test:headless": "ng test --watch=false --browsers=ChromeHeadless"
```

**5.** Change the `src/app/app.component.spec.ts` file and remove the tests `should have as title 'angular-travisci'` and `should render title`.

**6.** Run the test with the command below.

```shell
npm run test:headless

> angular-travisci@1.0.0 test:headless
> ng test --watch=false --browsers=ChromeHeadless

⠋ Generating browser application bundles (phase: setup)...Compiling @angular/core/testing : es2015 as esm2015
Compiling @angular/platform-browser/testing : es2015 as esm2015
Compiling @angular/compiler/testing : es2015 as esm2015
Compiling @angular/common/testing : es2015 as esm2015
Compiling @angular/router/testing : es2015 as esm2015
Compiling @angular/platform-browser-dynamic/testing : es2015 as esm2015
⠹ Generating browser application bundles (phase: building)...06 06 2021 21:22:49.870:INFO [karma-server]: Karma v6.3.3 server started at http://localhost:9876/
06 06 2021 21:22:49.872:INFO [launcher]: Launching browsers ChromeHeadless with concurrency unlimited
06 06 2021 21:22:49.875:INFO [launcher]: Starting browser ChromeHeadless
✔ Browser application bundle generation complete.
06 06 2021 21:22:54.562:INFO [Chrome Headless 91.0.4472.77 (Linux x86_64)]: Connected on socket SvdczBWd9ENbliBLAAAB with id 49624818
Chrome Headless 91.0.4472.77 (Linux x86_64): Executed 1 of 1 SUCCESS (0.059 secs / 0.036 secs)
TOTAL: 1 SUCCESS
```

**7.** Run the application with the command below. Access the URL `http://localhost:4200/` and check if the application is working.

```shell
npm start

> angular-travisci@1.0.0 start
> ng serve

✔ Browser application bundle generation complete.

Initial Chunk Files | Names         |      Size
vendor.js           | vendor        |   2.38 MB
polyfills.js        | polyfills     | 128.56 kB
main.js             | main          |   8.93 kB
runtime.js          | runtime       |   6.59 kB
styles.css          | styles        | 118 bytes

                    | Initial Total |   2.52 MB

Build at: 2021-06-07T00:23:57.046Z - Hash: 0ddc925fb2029ab1452c - Time: 8963ms

** Angular Live Development Server is listening on localhost:4200, open your browser on http://localhost:4200/ **


✔ Compiled successfully.
```

**8.** Build the application with the command below.

```shell
npm run build:prod

> angular-travisci@1.0.0 build:prod
> ng build --configuration production --base-href https://rodrigokamada.github.io/angular-travisci/

✔ Browser application bundle generation complete.
✔ Copying assets complete.
✔ Index html generation complete.

Initial Chunk Files           | Names         |      Size
main.c678fa8750e7c769.js      | main          | 177.63 kB
polyfills.6d7801353e02e327.js | polyfills     |  36.21 kB
runtime.b136bda8a38c4f2e.js   | runtime       |   1.06 kB
styles.ef46db3751d8e999.css   | styles        |   0 bytes

                              | Initial Total | 214.90 kB

Build at: 2021-09-05T22:42:19.525Z - Hash: 83bfffc079b083727ca4 - Time: 26030ms
```

**9.** Syncronize the application on the GitHub repository that was created.

**10.** Ready! After synchronizing the application on the GitHub repository, Travis CI build the application and synchronize on the branch `gh-pages`. Access the URL `https://rodrigokamada.github.io/angular-travisci/` and check if the application is working. Replace the `rodrigokamada` value with your GitHub username.



## Cloning the application

**1.** Clone the repository.

```shell
git clone git@github.com:rodrigokamada/angular-travisci.git
```

**2.** Install the dependencies.

```shell
npm ci
```

**3.** Run the application.

```shell
npm start
```
