pipeline {
    agent any
    stages {

      stage('clean the application'){
                steps{
                    sh 'mvn test'
                }
            }
        stage('test the application'){
            steps{
                sh 'mvn test'
            }

            post {
                success {
                  echo "uploading the test report "
                   junit 'target/surefire-reports/*.xml'
                }

            }
        }
          stage('save build into artifacts') {
                    steps {
                        sh 'mvn package'
                    }
                    post {
                        success {
                            echo "Now Archiving the Artifacts...."
                            archiveArtifacts artifacts: '**/*.war'
                        }
                    }
                }

    }
}