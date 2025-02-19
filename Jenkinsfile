pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment { 
        packageVesion = ''
        nexusURL = '172.31.37.164:8081'
    }
    options {
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds()
    }
    // parameters {
    //     string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

    //     text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

    //     booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

    //     choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

    //     password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    // }
    // build
    stages {
        stage('Get the version') {
            steps {
                script{
                    def packageJson = readJSON file: 'package.json'
                    packageVesion = packageJson.version
                    echo "application version is $packageVesion"
                }
            }
        }
        stage('Install dependencies') {
            steps {
                sh """
                    npm install
                """
            }
        }
        stage('Build') {
            steps {
                sh """
                    ls -la
                    zip -q -r catalogue.zip ./* -x ".git" -x "*.zip"
                    ls -ltr
                """
            }
        }
        // stage('Publish artifacts') {
        //     steps {
        //         nexusArtifactUploader(
        //             nexusVersion: 'nexus3',
        //             protocol: 'http',
        //             nexusUrl: "${nexusURL}",
        //             groupId: 'com.roboshop',
        //             version: "${packageVesion}",
        //             repository: 'catalogue',
        //             credentialsId: 'nexus-auth',
        //             artifacts: [
        //                 [artifactId: 'catalogue',
        //                     classifier: '',
        //                     file: 'catalogue.zip',
        //                     type: 'zip']
        //             ]
        //         )
        //     }
        // }
        stage('Deploy') {
            steps {
                sh """
                    echo " Here i wrote shell script"
                    #sleep 10
                """
            }
        }
    }
    // Post build means build ipoena tharuwatha em cheyali
    post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }
        failure { 
            echo 'This runs when pipeline is failed , used generally to send some alerts !'
        }
        success { 
            echo 'I will say Hello when pipeline is success !'
        }
    }
}