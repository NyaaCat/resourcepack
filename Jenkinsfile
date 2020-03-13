pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'zip -9 -r nyaacat-resourcepack-${BUILD_NUMBER}.zip pack.mcmeta LICENSE assets'
            }
        }
    }
    post {
           always {
               archiveArtifacts artifacts: '*.zip', fingerprint: true
               cleanWs()
           }
    }
}
