#!groovy
@Library('roboshop-shared-library') _

//responsibility is to pass what type of application and component is this to pipeline decision

//creating variable

def configMap = [
    application: "nodejsVM",
    component: "catalogue"
]

if( ! env.BRANCH_NAME.equalsIgnoreCase('main')){
    pipelineDecission.decidePipeline(configMap)
}
else{
    echo"This is PRODUCTION, deal with CR process"
}
