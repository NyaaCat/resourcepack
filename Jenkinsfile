pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'sed -i "s/{version}/${BUILD_NUMBER}/g" pack.mcmeta'
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
