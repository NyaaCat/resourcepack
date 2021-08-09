pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                dir("pack/full") {
                    sh 'sed -i "s/{version}/${BUILD_NUMBER}/g" pack.mcmeta'
                    sh 'zip -9 -r inf-resourcepack-v3full-build${BUILD_NUMBER}.zip pack.png pack.mcmeta LICENSE assets'
                    sh 'cp inf-resourcepack-v3full-build${BUILD_NUMBER}.zip ../../'
                    sh 'cp inf-resourcepack-v3full-build${BUILD_NUMBER}.zip ../../inf-resourcepack-v3full-latest.zip'
                }
                dir("pack/lite") {
                    sh 'sed -i "s/{version}/${BUILD_NUMBER}/g" pack.mcmeta'
                    sh 'zip -9 -r inf-resourcepack-v3lite-build${BUILD_NUMBER}.zip pack.png pack.mcmeta LICENSE assets'
                    sh 'cp inf-resourcepack-v3lite-build${BUILD_NUMBER}.zip ../../'
                    sh 'cp inf-resourcepack-v3lite-build${BUILD_NUMBER}.zip ../../inf-resourcepack-v3lite-latest.zip'
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
