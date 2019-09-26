# Integration Application Definition of Done (IA-DoD) template
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
