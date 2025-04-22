pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/asthatomar2k1/TestRepositoryHO.git'
            }
        }
        stage('Run JMeter Test') {
            steps {
                bat 'jmeter -n -t JpetScript.jmx -l result.jtl'
            }
        }
    }
    post {
        always {
            emailext (
                subject: "Build ${currentBuild.fullDisplayName} - ${currentBuild.result}",
                body: "Build ${currentBuild.fullDisplayName} completed with status: ${currentBuild.result}",
                recipientProviders: [[$class: 'DevelopersRecipientProvider']]
            )
        }
    }
}
