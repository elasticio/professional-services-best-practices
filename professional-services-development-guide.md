# Elastic.io Professional services team Development guide

* [Component development](#component-development)
  * [Component development prerequisites](#component-development-prerequisites)
  * [Component Development Definition of Done (CD-DoD)](#component-development-definition-of-done-cd-dod)
    * [Component Development Process](#component-development-process)
    * [Component Development Quality Assurance](#component-development-quality-assurance)
    * [Sprint Review (Demo) Definition of Done (SR-DoD)](#sprint-review-demo-definition-of-done-sr-dod)
    * [Tests](#tests)
      * [Unit tests](#unit-tests)
      * [Integration Tests](#integration-tests)
    * [Logging](#logging)
    * [Credentials](#credentials)
    * [component.json](#componentjson)
    * [package.json](#packagejson)
    * [Logo](#logo)
    * [License](#license)
    * [Git](#git)
    * [Automated Build Tools](#automated-build-tools)
* [Integration application development](#integration-application-development)
  * [Integration application development prerequisites](#integration-application-development-prerequisites)
  * [Integration application Definition of Done (IA-DoD)](#integration-application-definition-of-done-ia-dod)
    * [Integration application Development Process](#integration-application-development-process)
    * [Integration application Quality Assurance](#integration-application-quality-assurance)
* [Code Library development](#code-library-development)
  * [Code Library development prerequisites](#code-library-development-prerequisites)
  * [Code Library Definition of Done (CL-DoD)](#code-library-definition-of-done-cl-dod)
    * [Code Library Development Process](#code-library-development-process)
    * [Code Library Quality Assurance](#code-library-quality-assurance)
* [Coding style](#coding-style)
  * [JavaScript Coding Style](#javascript-coding-style)
    * [Code Quality](#code-quality)
    * [Package.json](#packagejson)
    * [Default Libraries](#default-libraries)
  * [Java Coding Style](#java-coding-style)
    * [Static code analysis](#static-code-analysis)
    * [Test coverage](#test-coverage)
* [Templates](#templates)
  * [Component Development Definition of Done (CD-DoD) template](#component-development-definition-of-done-cd-dod-template)
  * [README.md template](#readmemd-template)
    * [Standard action/trigger description](#standard-actiontrigger-description)
  * [Integration Application Definition of Done (IA-DoD) template](#integration-application-definition-of-done-ia-dod-template)
  * [Code library Definition of Done (CL-DoD) template](#code-library-definition-of-done-cl-dod-template)

## Component development 
### Component development prerequisites
 * Development team has all needed requirements
 * Access to the needed service with all needed permissions is granted
 * No open tasks that could block Component development process
 * The E.io’s GitHub repository must be checked if there is another implementation of the component under development. If it exists, new repository should not be created
 * Component architecture should be discussed and approved before start coding.
 * New component GIT repo preconditions:
   - repo type (private/public)
   - license type
 * Component deployment preconditions:
   - Where to deploy (app.elastic.io etc..)
   - Component's access level on each installation that component must be deployed on
 
### Component Development Definition of Done (CD-DoD)
You can find a [CD-DoD template here](#component-development-definition-of-done-cd-dod-template). It can be (should be) put into a GitHub issue so that each item could be checked and marked as Done.
#### Component Development Process
* Code is written and formatted in accordance with the [Styling guide](#coding-style)
* Code (incl. configs, test samples, environment variables etc.) MUST NOT contain any sensitive data like passwords, tokens, API keys etc.
* Component logs does not contain any sensitive data (credentials, input/output requests, Environment variables)
* Code is covered with unit tests
* Component code is covered with integration tests (optional)
* Triggers/actions comply with OIH patterns
* Documentation (README.md file in the Github) is 100% ready
* Changelogs (CHANGELOG.md) are created/updated.
* Component's version is updated in `package.json` according to [Semantic Versioning 2.0.0](https://semver.org/)
* CI is set up
* All development branches are reviewed.

**After QA:**
* All development branches are merged into master branch
* Sprint review preparation is finished (demo flow is built)

#### Component Development Quality Assurance
* Test cases for the component are ready at the TestRail.
* Functional testing is finished.
* Regression testing is finished (optional).
* Component is deployed to the production stage (app.elastic.io) and/or other required stage.
  * Component has a proper access level
  * Required Environment Variables are set
  * Smoke test is finished
* Release notes is done
* Component Roadmap is updated.
* Component spreadsheet is updated

### Sprint Review (Demo) Definition of Done (SR-DoD)
* The component is deployed to a production system (e.g. [app.elastic.io](https://app.elastic.io)) or other tenant (if needed)
* Demo-flow is created before demo
* Name of demo-flow is meaningful and understandable and displays the purpose of the action/trigger (don't use 'Give me a name')
* Demo-flow represents real use-case of the component
* Timer component is not used for actions
* All the env vars are created and configured
* `EIO_REQUIRED_RAM_MB` var is configured if needed
* Configure external systems if needed (create Items, Customers, enable web service access etc.).

### Tests
#### Unit tests
* Sample use cases
* Un-common edge cases
* Blocks of non-trivial code that doesn’t talk directly to the external system
* Tests to verify correct metadata transformation.

#### Integration Tests
* Designed to run against the API for the component
* Any data created during integration tests should indicate that it was created by integration tests
* Any data that needs to be read from the API should be flagged in the test system that it is relied upon in integration tests.

### Logging
* Don’t log any credential
* Don’t log the data itself as it is moving through our system.

### Credentials
The following pieces of information should be stored in credentials in [BitWarden](https://bitwarden.com) (or any other):
* Credentials to elastic.io’s test instance
* A note which can be used as a .env file for running integration tests
* OAuth keys (including any test keys) (if applicable).

### component.json
* There should be a description for the component
* Each action & trigger should have a description
* Each config field for the credentials, actions and triggers should have a note and placeholder unless obvious (such as for a password)

### package.json
* Component version must be specified accordingly, please visit [Semantic Versioning 2.0.0](https://semver.org/) in order to do it in right way
* Specify dependencies with only specific versions. Dependency ```version``` Must match ```version``` exactly

### CHANGELOG.md
Complete changelogs in accordance with the [keepachangelog.com](https://keepachangelog.com/en/1.0.0/) 

### Logo
* The logo file should be a 128 x 128 px PNG file on a transparent background.

### License
* When code is open sourced, it should be released under the Apache 2.0 License
* The LICENSE file checked into Git should reference elastic.io’s copyright of the code and contain a link to the full text of the Apache 2.0 license, not the original license text.  [See this example](https://github.com/openintegrationhub/jdbc-component/blob/master/LICENSE)
* Not all components will be open sourced as in the future we may introduce a premium tier of components
* When code is closed source, the LICENSE file should reference elastic.io’s copyright of the code.  [See this example](https://github.com/elasticio/moodle-component/blob/master/LICENSE).

### Git
* Squash and merge should be used on merges after a PR.  Ideally, GitHub should be configured so that this is the default
* Delete branches once merged through a PR
* A .gitignore file should be checked in that keeps files and folders such as node_modules and .idea folders from being checked in
* Whitespace should be consistent through automated tools such as .editorconfig and .gitattribues files.

### Automated Build Tools
There are two automated build tools used at elastic.io:
* [Circle CI](https://circleci.com/dashboard) for closed source repositories
* [Travis CI](https://travis-ci.org/) for open source repositories.

Notes for automated build tools:
* Login to build tools is through your GitHub account
* Build may have to be enabled the first time by someone with admin permissions in GitHub
* Depending on the build tool, additional config files may have to be checked into source code. (e.g. .circleci & circle.yml for CircleCI, .travis.yml for Travis CI)
* Environment variables need to be configured in the build
* Build tools produce badge icons that can be embedded in the Readme (should be embedded if the tool is used).

## Integration application development
### Integration application development prerequisites
* PS team has access to the source with all requirements
* Meeting with Platform team representatives (for example Scrum Master) regarding E.IO platform changes (API etc.), which could potentially affect on Integration application development process
* Access to the needed services with all needed permissions is granted
* No open tasks that could block Integration application development process
* Integration application architecture should be discussed and approved before starting coding.

### Integration application Definition of Done (IA-DoD)
You can find an [IA-DoD template here](#integration-application-definition-of-done-ia-dod-template). It can be (should be) put into a GitHub issue so that each item could be checked and marked as Done.
#### Integration application Development Process
* Code is written and formatted in accordance with the Styling guide
* Code (incl. configs, test samples, environment variables etc.) MUST NOT contain any sensitive data like passwords, tokens, API keys etc.
* Integration application logs does not contain any sensitive data (if needed due to requirements)
* Code is covered with unit tests
* Code is covered with integration tests
* Continuous deployment:
  * Publish script
  * Secrets
  * k8s descriptors
* Documentation 
  * Readme.md with sequence diagrams, overview, description and installation manual
  * Environment variables listing and description (env-vars.md) Changelogs (CHANGELOG.md). 

**After QA:**
* All development branches are reviewed and merged into master branch
* Sprint review preparation is finished.

#### Integration application Quality Assurance
* Test cases for the Integration application are ready at the TestRail
* Functional testing is finished
* Regression testing is finished (optional)
* Integration application is deployed to the required stage
  * Smoke test is finished
* Release notes is done.

## Code Library development
### Code Library development prerequisites
* PS team has access to the source with all requirements
* Meeting with Platform team representatives regarding Code Library re-usability
* Access to the needed services/code with all needed permissions is granted
* No open tasks that could block Code Library development process
* Code Library architecture should be discussed and approved before start coding.

### Code Library Definition of Done (CL-DoD)
You can find a [CL-DoD template here](#code-library-definition-of-done-cl-dod-template). It can be (should be) put into a GitHub issue so that each item could be checked and marked as Done.
#### Code Library Development Process
* Code is written and formatted in accordance with the Styling guide
* Code (incl. configs, test samples, environment variables etc.) MUST NOT contain any sensitive data like passwords, tokens, API keys etc.
* Code Library logs does not contain any sensitive data (if needed due to requirements)
* Code is covered with unit tests
* Code is covered with integration tests
* Continuous Integration is set up for tests
* Documentation 
  * Readme.md with sequence diagrams, overview, description
  * Changelogs (CHANGELOG.md) 
* All development branches are reviewed, merged into master branch and deleted
* Code Library is pushed to:
  * Mvn repo (for Java)
  * Npm (for Node.js)
* Sprint review preparation is finished.

#### Code Library Quality Assurance
* Code Library will be only tested in affected components/integration applications due to the complexity of Code Library testing itself.

## Coding style
>Always code as if the guy who ends up maintaining your code will be a violent psychopath who knows where you live. – Rick Osborne

This document describes practices and opinionated set of conventions for the Java and JavaScript programming languages. 
It is strongly recommended for use by software engineers in Elastic.io PS team working on component building.
Goals
* Formalize development process
* Increase a speed of development process 
* Reduce an amount of errors and bugs
* Implemented coding styles and best practices significantly improve code readability, maintainability and allows to produce more bugs-free code.

### JavaScript Coding Style
#### Code Quality
* [The async/await keyword combination pair is the preferred way to handle async code.](https://codeburst.io/async-patterns-in-node-js-only-4-different-ways-to-do-it-70186ee83250?gi=92953dd8e280)
  *  [Related reading on Node’s event loop/concurrency handling](https://blog.risingstack.com/node-js-at-scale-understanding-node-js-event-loop/)
* Code (in dependency libraries) that is callback based should use promisify to allow the use of await
* Const is preferred over let.  Using var or undeclared variables should be avoided.
* Currently Version 8 of Node.js is the preferred version
* Eslint shout be used to enforce code quality/act as an early detector of bugs
  * [The platform team uses eslint:recommended with plugin:node/recommended](https://github.com/elasticio/capybara/blob/master/.eslintrc)
  * Eslint may also require plugins for [mocha](https://www.npmjs.com/package/eslint-plugin-mocha) and [Sinon](https://www.npmjs.com/package/eslint-plugin-sinon)
* Code structure should be as follows:
  * verifyCredentials.js should be at the root of the repo
  * A lib folder should contain component code & static schemas
    * Any code that is in common between actions & triggers should be in the root of the lib folder
    * There should be a folder for actions, triggers and schemas respectively
  * A spec folder for unit tests which do not talk to external systems
  * A spec-integration folder for automated tests which communicate with the external system

#### Package.json
* Package-lock.json should be checked into source code
* Version references in package.json should be exact and not use the ^ or ~ character.
* A [pretest script](https://docs.npmjs.com/misc/scripts) should be used to enforce linting. (e.g. eslint verifyCredentials.js lib spec spec-integration --fix) and possibly dependency security vulnerabilities with [npm audit](https://docs.npmjs.com/cli/audit) (previously [nsp](https://www.npmjs.com/package/nsp) was used in some components)
* A “test” script for integration tests (e.g. mocha spec)
* An integration-test script for integration tests (e.g. “mocha spec-integration”)
* Author, keywords, files, engines, name, version and private should be set appropriately

#### Default Libraries
* HTTP requests should be made with [request.js](https://www.npmjs.com/package/request)
* Unit tests should be run with [mocha.js](https://mochajs.org/)
* Assertions should be done with [chai’s expect framework](https://www.chaijs.com/api/bdd/)
* Config values for integration tests should be read in with [dot-env](https://www.npmjs.com/package/dot-env)
* Spies, stubs & mocks should be done with [sinon.js](https://sinonjs.org/) (e.g. creating a mock emitter)
* Logging should be done by [debug](https://www.npmjs.com/package/debug)

### Java Coding Style
The proposed style to follow is Google recommended one: [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)

There are settings files containing these rules which can be downloaded and imported into IDE (IntelliJ Idea and Eclipse). 
Here is a short installation guide: 
[Installing the google styleguide settings in intellij and eclipse](https://github.com/HPI-Information-Systems/Metanome/wiki/Installing-the-google-styleguide-settings-in-intellij-and-eclipse)

After importing, a developer can format the code automatically with a keyboard shortcut (e.g. Alt+Shift+F).
It is recommended to use [CheckStyle-IDEA plugin](https://plugins.jetbrains.com/plugin/1065-checkstyle-idea) to use both real-time and on-demand scanning of Java files.

#### Static code analysis
All the code before the pull-request should be analyzed with static analyzing tools.

Recommended tools to use:

[PMDPlugin](https://plugins.jetbrains.com/plugin/1137-pmdplugin). Plugin to run static analysis using PMD in intelliJ.

[FindBugs-IDEA](https://plugins.jetbrains.com/plugin/3847-findbugs-idea). Provides static bytecode analysis to look for bugs in Java code from within IntelliJ IDEA. FindBugs is a defect detection tool for Java that uses static analysis to look for more than 200 bug patterns, such as null pointer dereferences, infinite recursive loops, bad uses of the Java libraries and deadlocks.

#### Test coverage
The code before being pull-requested must be covered with unit tests as much as possible. 
To achieve easy test coverage the code should be written (or accordingly refactored) with [SOLID, KISS](https://en.wikipedia.org/wiki/KISS_principle) principles in mind. Appropriate design patterns should be used if needed as well.
The code coverage percentage is another point to discuss and agree. But it should be as close to 100% as possible.

## Templates
Templates to paste into each (main, not sub-) GitHub task in order to check the readiness

### Component Development Definition of Done (CD-DoD) template
\*\*DoD**

\*\*Component development prerequisites:\*\*

\- [ ] Development team has all needed requirements\
\- [ ] Access to the needed service with all needed permissions is granted\
\- [ ] No open tasks that could block Component development process\
\- [ ] The E.io’s GitHub repository must be checked if there is another implementation of the component under development. If it exists, new repository should not be created\
\- [ ] Component architecture should be discussed and approved before start coding\
\- [ ] New component GIT repo preconditions:\
&nbsp;&nbsp;- repo type (private/public)\
&nbsp;&nbsp;- license type\
\- [ ] Component deployment preconditions:\
&nbsp;&nbsp;- Where to deploy (app.elastic.io etc..)\
&nbsp;&nbsp;- Component's access level on each installation that component must be deployed on\

\*\*Development:\*\*

\- [ ] Code is written and formatted in accordance with the Styling guide\
\- [ ] Code (incl. configs, test samples, environment variables etc.) MUST NOT contain any sensitive data like passwords, tokens, API keys etc.\
\- [ ] Component logs does not contain any sensitive data (credentials, input/output requests, Environment variables)\
\- [ ] Code is covered with unit tests\
\- [ ] Component code is covered with integration tests (optional)\
\- [ ] Triggers/actions comply with OIH patterns\
\- [ ] Documentation (README.md file in the Github) is 100% ready\
\- [ ] Changelogs (CHANGELOG.md) are created/updated\
\- [ ] Component's version is updated in `package.json` according to [Semantic Versioning 2.0.0](https://semver.org/)\
\- [ ] CI is set up\
\- [ ] All development branches are reviewed

\*\*After QA:\*\*

\- [ ] All development branches are merged into master branch\
\- [ ] Sprint review preparation is finished (demo flow is built)

\*\*QA:\*\*

\- [ ] Test cases for the component are ready at the TestRail\
\- [ ] Functional testing is finished\
\- [ ] Regression testing is finished (optional)\
\- [ ] Component is deployed to the production stage (app.elastic.io) and/or other required stage\
&nbsp;&nbsp;- Component has a proper access level\
&nbsp;&nbsp;- Required Environment Variables are set\
&nbsp;&nbsp;- Smoke test is finished\
\- [ ] Release notes is done\
\- [ ] Component Roadmap is updated\
\- [ ] Component spreadsheet is updated

### README.md template

`[![CircleCI](https://circleci.com/gh/elasticio/component)](https://circleci.com/gh/elasticio/component)`
`[![Build Status][travis-image]][travis-url]`

\# Component name\
\## Table of Contents

```
* [General information](#general-information)
   * [Description](#description)
   * [Purpose](#purpose)
   * [Completeness Matrix](#completeness-matrix)
   * [How works](#how-works)
   * [API version](#api-version)
* [Requirements](#requirements)
   * [Environment variables](#environment-variables)
* [Credentials](#credentials)
     * [<Field one description>](#field-one-description)
     * [<Field two description>](#field-two-description)
* [Triggers](#triggers)
   * [Trigger Name](#trigger-name)
     * [Trigger Name. Config fields](#trigger-name-config-fields)
* [Actions](#actions)
   * [Action Name](#action-name)
     * [Action Name. Config fields](#action-name-config-fields)
* [Additional info](#additional-info)
* [Known Limitations](#known-limitations)
* [<External System> API and Documentation links](#<external system>-api-and-documentation-links)
```
\## Description\
\### Purpose\
\### Completeness Matrix (Completeness Matrix Template)\
\### How works.  API version / SDK version\
\### Requirements\
\#### Environment variables\
\#### Others\
\## Credentials\
&nbsp;&nbsp;\### field1\
&nbsp;&nbsp;\### field2\
&nbsp;&nbsp;\...\
\## Triggers (if any)\
&nbsp;&nbsp;\### Trigger1\
&nbsp;&nbsp;&nbsp;&nbsp;\<Standard action/trigger description>\
&nbsp;&nbsp;\### Trigger2\
&nbsp;&nbsp;&nbsp;&nbsp;\<Standard action/trigger description>\
\## Actions (if any)\
&nbsp;&nbsp;\### Action1\
&nbsp;&nbsp;&nbsp;&nbsp;\<Standard action/trigger description>\
&nbsp;&nbsp;\### Action2\
&nbsp;&nbsp;&nbsp;&nbsp;\<Standard action/trigger description>\
\## Additional info (If any)\
\## Known limitations (common for the component)\
\## \<External System> API and Documentation links (endpoints)

#### Standard action/trigger description
\#### List of Expected Config fields\
\### Expected input metadata\
\#### Expected output metadata\
\#### Sample pseudo-code (optional)\
\#### Standardize Names (Human readable + Machine readable)\
\#### Known limitations for the particular trigger/action / Planned future stages\
\#### Authentication scopes\
\#### Links to documentation

### Integration Application Definition of Done (IA-DoD) template
\*\*DoD**

\*\*Integration application development prerequisites:\*\*

\- [ ] Development team has access to the source with all requirements\
\- [ ] Meeting with Platform team representatives (for example Scrum Master) regarding E.IO platform changes (API etc.), which could potentially affect on Integration application development process\
\- [ ] Access to the needed services with all needed permissions is granted\
\- [ ] No open tasks that could block Integration application development process\
\- [ ] Integration application architecture should be discussed and approved before starting coding

\*\*Development:\*\*

\- [ ] Code is written and formatted in accordance with the Styling guide\
\- [ ]Code (incl. configs, test samples, environment variables etc.) MUST NOT contain any sensitive data like passwords, tokens, API keys etc.\
\- [ ] Integration application logs does not contain any sensitive data (if needed due to requirements)\
\- [ ] Code is covered with unit tests\
\- [ ] Code is covered with integration tests\
\- [ ] Continuous deployment:\
&nbsp;&nbsp;- Publish script\
&nbsp;&nbsp;- Secrets\
&nbsp;&nbsp;- k8s descriptors\
\- [ ] Documentation:\
&nbsp;&nbsp;-  Readme.md with sequence diagrams, overview, description and installation manual\
&nbsp;&nbsp;- Environment variables listing and description (env-vars.md)\
&nbsp;&nbsp;- Changelogs (CHANGELOG.md)

\*\*After QA:\*\*

\- [ ] All development branches are reviewed and merged into master branch\
\- [ ] Sprint review preparation is finished.

\*\*QA:\*\*

\- [ ] Test cases for the Integration application are ready at the TestRail\
\- [ ] Functional testing is finished\
\- [ ] Regression testing is finished (optional)\
\- [ ] Integration application is deployed to the required stage\
\- [ ] Smoke test is finished\
\- [ ] Release notes is done

### Code library Definition of Done (CL-DoD) template
\*\*DoD**

\*\*Development:\*\*

\- [ ] Code is written and formatted in accordance with the Styling guide\
\- [ ] Code (incl. configs, test samples, environment variables etc.) MUST NOT contain any sensitive data like passwords, tokens, API keys etc.\
\- [ ] Code Library logs does not contain any sensitive data (if needed due to requirements)\
\- [ ] Code is covered with unit tests\
\- [ ] Code is covered with integration tests\
\- [ ] Continuous Integration is set up for tests\
\- [ ] Documentation\
&nbsp;\- Readme.md with sequence diagrams, overview, description\
&nbsp;\- Change-logs (CHANGELOG.md)\
\- [ ] All development branches are reviewed and merged into master branch and deleted\
\- [ ] Code Library is pushed to:\
&nbsp;\- mvn repo (for Java)\
&nbsp;\- npm (for Node.js)\
\- [ ] Sprint review preparation is finished
