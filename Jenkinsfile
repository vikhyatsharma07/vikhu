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
        }

          stage('crate the build '){
                    steps{
                        sh 'mvn package'
                    }
                }

        stage('deploy to tomcat ')
        {
            sshagent(['tomcat']) {
                  sh """
                    scp -o StrictHostKeyChecking=no targer/embeddedTomcatSample.war ubuntu@172.31.45.203/opt/tomcat/apache-tomcat-9.0.33/webapps

                    ssh ubuntu@172.31.45.203//opt/tomcat/apache-tomcat-9.0.33/bin/shutdown.sh

                    ssh ubuntu@172.31.45.203//opt/tomcat/apache-tomcat-9.0.33/bin/shartup.sh

                  """
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