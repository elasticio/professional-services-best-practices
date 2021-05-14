# Component Development Definition of Done (CD-DoD) template
\*\*DoD**

\*\*Component development prerequisites:\*\*

\- [ ] All the branches of the repo should be checked (merged/deleted if possible) before starting development\
\- [ ] Development team has all needed requirements\
\- [ ] Access to the needed service with all needed permissions is granted\
\- [ ] No open tasks that could block Component development process\
\- [ ] The E.io’s GitHub repository must be checked if there is another implementation of the component under development. If it exists, new repository should not be created\
\- [ ] Component architecture should be discussed and approved before start coding\
\- [ ] New component GIT repo preconditions:\
&nbsp;&nbsp;- repo type (private/public)\
&nbsp;&nbsp;- license type\

\*\*Development:\*\*

\- [ ] Code is written and formatted in accordance with the Styling guide\
\- [ ] Code (incl. configs, test samples, environment variables etc.) MUST NOT contain any sensitive data like passwords, tokens, API keys etc.\
\- [ ] Component logs does not contain any sensitive data (credentials, input/output requests, environment variables)\
\- [ ] Code is covered with unit tests\
\- [ ] Component code is covered with integration tests (optional)\
\- [ ] Triggers/actions comply with ex-OIH patterns\
\- [ ] Component documentation (currently README.md file in the Github) is 100% ready\
\- [ ] Changelogs (CHANGELOG.md) are created/updated:\
&nbsp;&nbsp;- Component's version is updated according to [Semantic Versioning 2.0.0](https://semver.org/)\
\- [ ] `package.json` or `build.gradle` is updated:\
&nbsp;&nbsp;- Component's version is updated according to [Semantic Versioning 2.0.0](https://semver.org/)\
&nbsp;&nbsp;- Component version in package.json should match component version in CHANGELOG.md\
\- [ ] Component should be dockerised, add: `"buildType":"docker"` line into `component.json`\
\- [ ] CI is set up\
\- [ ] All development branches are reviewed\
\- [ ] Support and documentation teams are notified about component updates in appropriate Slack channels\
\- [ ] A release for the component is created in a GitHub repository

\*\*After QA:\*\*

\- [ ] All needed development branches are merged into master branch\
\- [ ] Support is notified in #Support and #Docs channels that component is ready to be deployed and docs should be updated on docs.elastic.io after all needed development branches are merged into master branch\
\- [ ] Sprint review preparation is finished (demo flow is built)\

\*\*QA:\*\*

\- [ ] Test cases for the component are ready at the TestRail\
\- [ ] Functional testing is finished\
\- [ ] Regression testing is finished (optional)\
\- [ ] Release notes and Agenda are done\
\- [ ] Component spreadsheet is updated\
\- [ ] Smoke is done after component updated on Production\
\- [ ] Docs reviewed after support update them on docs.elastic.io\
