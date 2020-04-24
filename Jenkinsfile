pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'sed -i "s/{version}/${BUILD_NUMBER}/g" pack.mcmeta'
                sh 'zip -9 -r nyaacat-resourcepack-${BUILD_NUMBER}.zip pack.mcmeta LICENSE assets'
                sh 'cp nyaacat-resourcepack-${BUILD_NUMBER}.zip nyaacat-resourcepack-latest.zip'
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
