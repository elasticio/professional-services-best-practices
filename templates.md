# Templates
Templates to paste into each (main, not sub-) GitHub task in order to check the readiness
* [Component Development Definition of Done (CD-DoD) template](#component-development-definition-of-done-cd-dod-template)
* [README.md template](#readmemd-template)
* [Standard action/trigger description](#standard-actiontrigger-description)
* [Integration Application Definition of Done (IA-DoD) template](#integration-application-definition-of-done-ia-dod-template)
* [Code library Definition of Done (CL-DoD) template](#code-library-definition-of-done-cl-dod-template)



## Component Development Definition of Done (CD-DoD) template
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
\- [ ] `package.json` or `build.gradle` is updated:\
&nbsp;&nbsp;- Component's version is updated according to [Semantic Versioning 2.0.0](https://semver.org/)\
&nbsp;&nbsp;- Component should be dockerised, add: `"buildType":"docker"`\
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

## README.md template

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

## Standard action/trigger description
\#### List of Expected Config fields\
\### Expected input metadata\
\#### Expected output metadata\
\#### Sample pseudo-code (optional)\
\#### Standardize Names (Human readable + Machine readable)\
\#### Known limitations for the particular trigger/action / Planned future stages\
\#### Authentication scopes\
\#### Links to documentation

## Integration Application Definition of Done (IA-DoD) template
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

## Code library Definition of Done (CL-DoD) template
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
