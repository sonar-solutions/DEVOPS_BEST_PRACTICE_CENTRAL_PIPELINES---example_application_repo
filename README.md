# example-application-repo

This repository demonstrates the required Jenkinsfile structure for all application projects governed by the central DevOps pipeline.

## Jenkinsfile Structure
Your Jenkinsfile **must**:
- Only define variables needed for the central pipeline (e.g., SonarQube project key, organization, token, host URL).
- Call the central pipeline by checking out the central pipeline repository and running its Jenkinsfile.
- Not contain any other steps, commands, or custom logic.

**Example Jenkinsfile:**
```groovy
// Developer defines variables here
def SONAR_PROJECT_KEY = 'my-nodejs-express-api'
def SONAR_ORG = 'my-org'
def SONAR_TOKEN = credentials('sonar-token')
def SONAR_HOST_URL = 'https://sonarcloud.io'

// Run the pipeline from the central repo
dir('devopsteam-centralpipelines-repo') { git url: 'https://gitlab.com/your-group/devopsteam-centralpipelines-repo.git', branch: 'main' }
def pipelineScript = load 'devopsteam-centralpipelines-repo/Jenkinsfile'
pipelineScript.runPipeline(SONAR_PROJECT_KEY, SONAR_ORG, SONAR_TOKEN, SONAR_HOST_URL)
```

## Governance & Validation
- This repository is subject to strict governance.
- A Jenkinsfile validator job will automatically check that your Jenkinsfile follows the required template.
- Any Jenkinsfile that includes unauthorized steps or logic will be rejected and blocked from merging.

## Contact
For questions or help, contact the DevOps team.
