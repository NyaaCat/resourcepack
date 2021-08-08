pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                dir("pack") {
                    sh 'sed -i "s/{version}/${BUILD_NUMBER}/g" pack.mcmeta'
                    sh 'zip -9 -r nyaacat-resourcepack-v3l-${BUILD_NUMBER}.zip pack.png pack.mcmeta LICENSE assets'
                    sh 'cp nyaacat-resourcepack-v3l-${BUILD_NUMBER}.zip ../'
                    sh 'cp nyaacat-resourcepack-v3l-${BUILD_NUMBER}.zip ../nyaacat-resourcepack-v3l-latest.zip'
                }
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
