pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                sh './mvnw -Dmaven.test.failure.ignore=true clean verify'
            }
        }
        stage("Reports") {
            steps {
                allure results: [[path: 'target/allure-results']] commandline: 'allure-2.1.1'
            }
        }
    }
    post {
        always {
            deleteDir()
        }
    }
}
