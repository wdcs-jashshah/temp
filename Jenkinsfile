pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from version control
                checkout scm
            }
        }

        stage('Cloning Git') {
            steps {
                git([url: 'https://github.com/wdcs-jashshah/temp.git', branch: 'main'])
            }
        }

        stage('Build') {
            steps {
                // Your test steps go here
            }
        }

        stage('Test') {
            steps {
                // Clean before build
                cleanWs()
                // We need to explicitly checkout from SCM here
                checkout scm
                echo "Building ${env.JOB_NAME}..."
            }
        }
    }

        stage('Deploy') {
            steps {
                // Your deployment steps go here
            }
        }
    }

    post {
        always {
            cleanWs()
            cleanWs(cleanWhenNotBuilt: false,
                deleteDirs: true,
                disableDeferredWipeout: true,
                notFailBuild: true,
                patterns: [[pattern: '.gitignore', type: 'INCLUDE'],
                           [pattern: '.propsfile', type: 'EXCLUDE']])
        }
}
