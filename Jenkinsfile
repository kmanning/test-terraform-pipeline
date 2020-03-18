@Library(['terraform-pipeline@v5.5']) _

AwssumePlugin.init()
CrqPlugin.init()
AnsiColorPlugin.init()

Jenkinsfile.init(this)
Jenkinsfile.defaultNodeName = 'master'

def validate = new TerraformValidateStage()
def build = new BuildStage()
def deployQa = new TerraformEnvironmentStage('qa')
def regressionQa = new RegressionStage()
def deployUat = new TerraformEnvironmentStage('uat')
def deployProd = new TerraformEnvironmentStage('prod')

validate.then(build)
        .then(deployQa)
        .then(regressionQa)
        .then(deployUat)
        .then(deployProd)
        .build()
