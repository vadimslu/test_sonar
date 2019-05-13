//GLOBAL ENVs

def registry_url = 'http://sv66548.sunlifecorp.com:10443'
def image_build_agent = 'sv66548.sunlifecorp.com:10443/dte/weather-app'

pipeline {
    agent any

    environment {
        registry = "sv66548.sunlifecorp.com:10443"
        registryCredential = 'dtr_creds'
        image_name = 'sv66548.sunlifecorp.com:10443/dte/refference-weather-app-201812211600'
        tag    = 'current'
    }

    stages {
        stage('build user') {
      steps {
        wrap([$class: 'BuildUser']) {
          sh 'echo "${BUILD_USER}"'
                                   }
            }
         }
        stage('checkout') {
            steps {
                git credentialsId: 'BitBucket_User', url: 'http://gq60@bitbucket.sunlifecorp.com:7990/scm/edte/vadim_java_app.git', branch: 'master'
            }
        }
        stage('scan') {
            steps {
                        sh "/var/jenkins_home/sonar-scanner/bin/sonar-scanner /var/jenkins_home/workspace/SonarScan_Test/"

                  }
             }
        stage('push') {
            steps {
                    script {
                                echo "Step2"
                           }
                  }
                     }
        stage('deploy') {
            steps {
                        echo "This step will deploy image on cluster"
                  }
                     }
        stage('Remove Unused docker image') {
            steps {
                       echo "Step3"
                  }
                                             }
    }

}
