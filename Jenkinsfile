pipeline {

    agent any  
       stages {
          stage('Checkout Code') {
              steps {
                  checkout scm
               }
            }
          stage('Cloning Git'){
            steps {
              git([url: 'https://github.com/wdcs-jashshah/temp.git', branch: 'main'])

                  }
             }
             stages {
        stage('Build') {
            steps {
                // Clean before build
                cleanWs()
                // We need to explicitly checkout from SCM here
                checkout scm
                echo "Building ${env.JOB_NAME}..."
            }
        }
    }
    post {
        // Clean after build
        always {
            cleanWs(cleanWhenNotBuilt: false,
                    deleteDirs: true,
                    disableDeferredWipeout: true,
                    notFailBuild: true,
                    patterns: [[pattern: '.gitignore', type: 'INCLUDE'],
                               [pattern: '.propsfile', type: 'EXCLUDE']])
        }
    }
}
