// Developer defines variables here
def SONAR_PROJECT_KEY = 'my-nodejs-express-api'
def SONAR_ORG = 'my-org'
def SONAR_TOKEN = credentials('sonar-token')
def SONAR_HOST_URL = 'https://sonarcloud.io'

// Run the pipeline from the central repo
dir('devopsteam-centralpipelines-repo') { git url: 'https://bitbucket.com/your-group/devopsteam-centralpipelines-repo.git', branch: 'main' }
def pipelineScript = load 'devopsteam-centralpipelines-repo/Jenkinsfile'
pipelineScript.runPipeline(SONAR_PROJECT_KEY, SONAR_ORG, SONAR_TOKEN, SONAR_HOST_URL)
