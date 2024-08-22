pipeline {
    agent any
    stages {
        stage('Deploy to Astronomer') {
            when {
                expression {
                    return env.GIT_BRANCH == "origin/main" ||  env.GIT_BRANCH == "origin/develop"
                }
            }
            steps {
                checkout scm
                sh '''
                curl -LJO https://github.com/astronomer/astro-cli/releases/download/v1.28.1/astro_1.28.1_linux_amd64.tar.gz
                tar -zxvf astro_1.28.1_linux_amd64.tar.gz astro && rm astro_1.28.1_linux_amd64.tar.gz
                ./astro deploy env.ASTRONOMER_DEPLOYMENT_ID
                '''
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
