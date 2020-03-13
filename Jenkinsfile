pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mkdir -p out'
                sh 'zip -9 -r out/nyaacat-resourcepack-${BUILD_NUMBER}.zip pack.mcmeta LICENSE assets'
            }
        }
    }
    post {
           always {
               archiveArtifacts artifacts: 'out/*.zip', fingerprint: true
               cleanWs()
           }
    }
}
