pipeline {
      agent any
      stages {
            stage('package the  project ') {
                  steps {
                    sh 'mvn clean package'
                  }
            }
      }

        post {
                success {
                       archiveArtifacts artifacts: '**/*.war'
                      }
             }
}