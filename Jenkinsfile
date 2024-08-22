pipeline {
    agent any
    stages {
        stage('Insatall astro') {
            steps {
                checkout scm
                nodejs(nodeJSInstallationName: 'NodeJS') {
                    sh 'npm i'    
                }
            }
        }
        stage('Build astro') {
            steps {
                nodejs(nodeJSInstallationName: 'NodeJS') {
                    sh 'npm run build'
                }
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
