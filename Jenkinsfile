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
        stage('deploy to tomcat ')
        {


        }

    }
}