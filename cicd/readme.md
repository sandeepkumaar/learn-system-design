## Continuous Integration Continuous Deployment

### Continuous Integration 
- Process of facilitating continous code **merges** to the main branch through automated pipelines   
- Deals with branches

### Continuous Delivery
- Process of facilitating continous code **deployments** to production through automated pipelines
- Deals with Deployment Environments 

CI & CD are different process and their cadence change based on the requirement. Usuall Integration is continuos and Deployment follows a fixed cadence(release)

### Trunk Based Development with Release Tags (with optional Release branches)
Code Integrations during sprints
- main : test ->  functional test(mocks) -> build -> merge -> deploy(dev) - functional(actual) -> performance
- feature : test -> functional test(mocks)
features are merged to main 

Code Deployment 
- Create release tag from the `main` trunck - no need to run piplines or run any release specific. Deploy to UAT
- If any changes after UAT, create release branch, code on `main` and cherry pick from trunk to release branch. 
- release branch has same pipeline jobs as trunck

### Workflows 
- feature.yml
- main.yml & release.yml
- release-tag.yml (dispatch)








