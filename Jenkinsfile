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
        stage('Copy files to nginx') {
            steps {
                sh 'mkdir -p /jenkins_exports/astro-test && cp -r dist/* /jenkins_exports/astro-test/'
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
