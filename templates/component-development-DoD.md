# Component Development Definition of Done (CD-DoD) template
\*\*DoD**

\*\*Component development prerequisites:\*\*

\- [ ] All the branches if the repo should be checked (merged/deleted if possible) before starting development\
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
