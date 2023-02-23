pipeline {
    agent none
    stages {
        stage('checkout'){
            agent any
            steps{
                echo 'cloning...'
                git url: "https://github.com/lethalfb/projectubu"
            }
        }
        stage('codecompile') {
            agent any
            options {
                // Timeout counter starts BEFORE agent is allocated
                timeout(time: 1, unit: 'SECONDS')
            }
            steps {
                echo 'compiling'
                sh "mvn compile"
            }
        }
        stage('codetest'){
            agent any
            options {
                // Timeout counter starts BEFORE agent is allocated
                timeout(time: 1, unit: 'SECONDS')
            }
            steps{
                sh "mvn test"
                echo "testing was done"
            }
        }
        stage('codeQA'){
            agent any
            options {
                // Timeout counter starts BEFORE agent is allocated
                timeout(time: 1, unit: 'SECONDS')
            }
            steps{
                sh "mvn pmd:pmd"
            }
        }
        stage('codepackage'){
            agent any
            options {
                // Timeout counter starts BEFORE agent is allocated
                timeout(time: 1, unit: 'SECONDS')
            }
            steps{
                sh "mvn package"
            }
        }
    }
}
