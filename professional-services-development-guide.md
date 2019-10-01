# Elastic.io Professional Services Team Development Guide

## Table of Contents
* [Component Development](#component-development)
  * [Component Development Definition of Ready (CD-DoR)](#component-development-definition-of-ready-cd-dor)
  * [Definition of Done (CD-DoD)](#component-development-definition-of-done-cd-dod)
    * [Development Process](#component-development-process)
    * [Quality Assurance](#component-development-quality-assurance)
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
  * [Development Prerequisites](#integration-application-development-prerequisites)
  * [Definition of Done (IA-DoD)](#integration-application-definition-of-done-ia-dod)
    * [Development Process](#integration-application-development-process)
    * [Quality Assurance](#integration-application-quality-assurance)
* [Code Library development](#code-library-development)
  * [Development Prerequisites](#code-library-development-prerequisites)
  * [Code Library Definition of Done (CL-DoD)](#code-library-definition-of-done-cl-dod)
    * [Development Process](#code-library-development-process)
    * [Quality Assurance](#code-library-quality-assurance)
* [Coding Style/Conventions](#coding-style)
  * [JavaScript](#javascript-coding-style)
  * [Java](#java-coding-style)

# Component Development 
## Component Development Definition of Ready (CD-DoR)
 * Development team has all needed requirements
 * Access to the needed service with all needed permissions is granted
 * No open tasks that could block component development process
 * The E[]().io’s GitHub repository must be checked for another implementation of the component under development. If one exists, new repository should not be created
 * Component architecture should be discussed and approved before start coding.
 * New component GIT repo preconditions:
   - repo type (private/public)
   - license type
 * Component deployment preconditions:
   - Where to deploy (app.elastic.io etc..)
   - Component's access level on each installation that component must be deployed on
 
## Component Development Definition of Done (CD-DoD)
You can find the CD-DoD template in templates.md. It should be put into a GitHub issue so that each item could be checked and marked as Done.
### Component Development Process
* All the branches if the repo should be checked (merged/deleted if possible) before starting development.
* Code is written and formatted in accordance with the [styling guide](#coding-style)
* Code (incl. configs, test samples, environment variables etc.) MUST NOT contain any sensitive data like passwords, tokens, API keys etc.
* Component logs does not contain any sensitive data (credentials, input/output requests, Environment variables)
* Code is covered with unit tests
* Component code is covered with integration tests (optional)
* Triggers/actions comply with [OIH patterns](https://github.com/elasticio/Connectors/blob/master/Adapters/AdapterBehaviorStandardization/StandardizedActionsAndTriggers.md)
* Documentation (README.md file in the Github) is 100% ready
* Changelogs (CHANGELOG.md) are created/updated. We use [this format as a standard](https://github.com/facebook/react/blob/master/CHANGELOG.md)
* `package.json` or `build.gradle` is updated:
  * Component's version is updated according to [Semantic Versioning 2.0.0](https://semver.org/)
  * Component should be dockerised, add: `"buildType":"docker"`
* CI is set up (see more [here](#automated-build-tools))
* All development branches are reviewed.

After QA:
* All development branches are merged into master branch
* Sprint review preparation is finished, demo flow is built

### Component Development Quality Assurance
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

## Sprint Review (Demo) Definition of Done (SR-DoD)
* The component is deployed to a production system (e.g. [app.elastic.io](https://app.elastic.io)) or other tenant (if needed)
* Demo-flow is created before demo

Demo flow specifications:
* Name of demo-flow is meaningful and understandable and displays the purpose of the action/trigger (don't use 'Give me a name')
* Demo-flow represents real use-case of the component
* Timer component is not used for actions
* All the env vars are created and configured
* `EIO_REQUIRED_RAM_MB` var is configured if needed
* Configure external systems if needed (create Items, Customers, enable web service access etc.).

## Tests
### Unit tests
* Sample use cases
* Un-common edge cases
* Blocks of non-trivial code that doesn’t talk directly to the external system
* Tests to verify correct metadata transformation.

### Integration Tests
* Designed to run against the API for the component
* Any data created during integration tests should indicate that it was created by integration tests
* Any data that needs to be read from the API should be flagged in the test system that it is relied upon in integration tests.

## Logging
* Don’t log any credentials
* Don’t log the data itself as it is moving through our system.

## Credentials
The following pieces of information should be stored in credentials in [BitWarden](https://bitwarden.com) (or any other):
* Credentials to elastic.io’s test instance
* A note which can be used as a .env file for running integration tests
* OAuth keys (including any test keys), if applicable

## component.json
* There should be a description for the component
* Each action & trigger should have a description
* Each config field for the credentials, actions and triggers should have a note and placeholder unless obvious (such as for a password)

## package.json
* Component version must be specified accordingly, please visit [Semantic Versioning 2.0.0](https://semver.org/) for more details on how to do this correctly
* Specify dependencies with only specific versions. Dependency ```version``` must match ```version``` exactly

## CHANGELOG.md
Complete changelogs in accordance with the [keepachangelog.com](https://keepachangelog.com/en/1.0.0/) 

## Logo
* The logo file should be a 128 x 128 px PNG file on a transparent background.

## License
* When code is open sourced, it should be released under the Apache 2.0 License
* The LICENSE file checked into Git should reference elastic.io’s copyright of the code and contain a link to the full text of the Apache 2.0 license, not the original license text.  [See this example](https://github.com/openintegrationhub/jdbc-component/blob/master/LICENSE)
* Not all components will be open sourced as in the future we may introduce a premium tier of components
* When code is closed source, the LICENSE file should reference elastic.io’s copyright of the code.  [See this example](https://github.com/elasticio/moodle-component/blob/master/LICENSE).

## Git
* Squash and merge should be used on merges after a PR.  Ideally, GitHub should be configured so that this is the default
* Delete branches once merged through a PR
* A .gitignore file should be checked in that keeps files and folders such as node_modules and .idea folders from being checked in
* Whitespace should be consistent through automated tools such as .editorconfig and .gitattribues files.

## Automated Build Tools
There are two automated build tools used at elastic.io:
* [Circle CI](https://circleci.com/dashboard) for closed source repositories
* [Travis CI](https://travis-ci.org/) for open source repositories.
Login to build tools is through your GitHub account

Notes for automated build tools:
* Builds may have to be enabled the first time by someone with admin permissions in GitHub
* Depending on the build tool, additional config files may have to be checked into source code. (e.g. .circleci & circle.yml for CircleCI, .travis.yml for Travis CI)
* Environment variables need to be configured in the build
* Build tools produce badge icons that should be embedded into a component's README
  * [Details for Circle CI](https://circleci.com/docs/2.0/status-badges/)
  * [Details for Travis CI](https://docs.travis-ci.com/user/status-images/)

# Integration application development
## Integration application development prerequisites
* PS team has access to the source with all requirements
* Meeting with Platform team representatives (for example Scrum Master) regarding E[]().IO platform changes (API etc.), which could potentially affect on Integration application development process
* Access to the needed services with all needed permissions is granted
* No open tasks that could block Integration application development process
* Integration application architecture should be discussed and approved before starting coding.

## Integration application Definition of Done (IA-DoD)
You can find an IA-DoD template in templates.md. It should be put into your GitHub issue so that each item could be checked and marked as Done.
### Integration application Development Process
* Code is written and formatted in accordance with the styling guide
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

After QA:
* All development branches are reviewed and merged into master branch
* Sprint review preparation is finished.

### Integration application Quality Assurance
* Test cases for the Integration application are ready at the TestRail
* Functional testing is finished
* Regression testing is finished (optional)
* Integration application is deployed to the required stage
  * Smoke test is finished
* Release notes is done.

# Code Library development
## Code Library development prerequisites
* PS team has access to the source with all requirements
* Meeting with Platform team representatives has occurred regarding Code Library re-usability
* Access to the needed services/code with all needed permissions is granted
* No open tasks that could block Code Library development process
* Code Library architecture should be discussed and approved before start coding.

## Code Library Definition of Done (CL-DoD)
You can find a CL-DoD template in templates.md. It should be put into your GitHub issue so that each item could be checked and marked as Done.
### Code Library Development Process
* Code is written and formatted in accordance with the [styling guide](#coding-style)
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

### Code Library Quality Assurance
* Code Library will be only tested in affected components/integration applications due to the complexity of Code Library testing itself.

# Coding Style/Conventions
> Always code as if the guy who ends up maintaining your code will be a violent psychopath who knows where you live. – Rick Osborne

This document describes practices and opinionated set of conventions for the Java and JavaScript programming languages. 
It is strongly recommended for use by software engineers in Elastic.io PS team working on component building.
Goals
* Formalize development process
* Increase a speed of development process 
* Reduce an amount of errors and bugs
* Implemented coding styles and best practices significantly improve code readability, maintainability and allows to produce more bugs-free code.

## JavaScript Coding Style
### Code Quality
* Eslint shout be used to enforce code quality/act as an early detector of bugs
  * The PS team follows Airbnb style guidelines: [see more here](https://github.com/airbnb/javascript)
    * [Here are the PS team WebStorm settings](https://github.com/elasticio/ps-webstorm-settings)
  * Eslint may also require plugins for [mocha](https://www.npmjs.com/package/eslint-plugin-mocha) and [sinon](https://www.npmjs.com/package/eslint-plugin-sinon)
* Async code should ideally be handled using async/await functions in a try/catch block
  * [Example](https://codeburst.io/async-patterns-in-node-js-only-4-different-ways-to-do-it-70186ee83250?gi=92953dd8e280)
  *  [Related reading on Node’s event loop/concurrency handling](https://blog.risingstack.com/node-js-at-scale-understanding-node-js-event-loop/)
* Code (in dependency libraries) that is callback based should use promisify to allow the use of await
* Const is preferred over let.  Using var or undeclared variables should be avoided.
* Node.js v8 is the current standard

### Typical file structure for components in node.js
    .
    ├── ...
    ├── lib                
    │   ├── actions          
    │   ├── triggers
    │   └── ...               
    ├── spec                    
    ├── spec-integration  
    ├── verifyCredentials.js
    ├── component.json 
    └── ...

* verifyCredentials.js should be at the root of the repo
* A lib folder should contain component code & static schemas
  * Any code that is in common between actions & triggers should be in the root of the lib folder
  * There should be a folder for actions, triggers and schemas respectively
  * All actions and triggers need a main `process` function 
* A spec folder for unit tests which do not talk to external systems
* A spec-integration folder for automated tests which communicate with the external system

### Package.json
* Package-lock.json should be checked into source code
* Version references in package.json should be exact and not use the ^ or ~ character.
* A [pretest script](https://docs.npmjs.com/misc/scripts) should be used to enforce linting. (e.g. eslint verifyCredentials.js lib spec spec-integration --fix) and possibly dependency security vulnerabilities with [npm audit](https://docs.npmjs.com/cli/audit) (previously [nsp](https://www.npmjs.com/package/nsp) was used in some components)
* A “test” script for integration tests (e.g. mocha spec)
* An integration-test script for integration tests (e.g. “mocha spec-integration”)
* Author, keywords, files, engines, name, version and private should be set appropriately

### Default Libraries and Testing
* HTTP requests should be made with [request.js](https://www.npmjs.com/package/request)
* Unit tests should be run with [mocha.js](https://mochajs.org/)
* Assertions should be done with [chai’s expect framework](https://www.chaijs.com/api/bdd/)
* Config values for integration tests should be read in with [dot-env](https://www.npmjs.com/package/dot-env)
* Spies, stubs & mocks should be done with [sinon.js](https://sinonjs.org/) (e.g. creating a mock emitter)
* Logging should be done by [debug](https://www.npmjs.com/package/debug)

## Java Coding Style
The proposed style to follow is Google recommended one: [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)

There are settings files containing these rules which can be downloaded and imported into IDE (IntelliJ Idea and Eclipse). 
Here is a short installation guide: 
[Installing the google styleguide settings in intellij and eclipse](https://github.com/HPI-Information-Systems/Metanome/wiki/Installing-the-google-styleguide-settings-in-intellij-and-eclipse)

After importing, a developer can format the code automatically with a keyboard shortcut (e.g. Alt+Shift+F).
It is recommended to use [CheckStyle-IDEA plugin](https://plugins.jetbrains.com/plugin/1065-checkstyle-idea) to use both real-time and on-demand scanning of Java files.

### Static code analysis
All the code before the pull-request should be analyzed with static analyzing tools.

Recommended tools to use:

[PMDPlugin](https://plugins.jetbrains.com/plugin/1137-pmdplugin). Plugin to run static analysis using PMD in intelliJ.

[FindBugs-IDEA](https://plugins.jetbrains.com/plugin/3847-findbugs-idea). Provides static bytecode analysis to look for bugs in Java code from within IntelliJ IDEA. FindBugs is a defect detection tool for Java that uses static analysis to look for more than 200 bug patterns, such as null pointer dereferences, infinite recursive loops, bad uses of the Java libraries and deadlocks.

### Test coverage
The code before being pull-requested must be covered with unit tests as much as possible. 
To achieve easy test coverage the code should be written (or accordingly refactored) with [SOLID, KISS](https://en.wikipedia.org/wiki/KISS_principle) principles in mind. Appropriate design patterns should be used if needed as well.
The code coverage percentage is another point to discuss and agree. But it should be as close to 100% as possible.
