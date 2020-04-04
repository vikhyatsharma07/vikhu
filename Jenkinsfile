pipeline {

agent any

    stages{

            stage('clean the code ')
            {
                steps{
                    sh 'mvn clean'
                }
            }

            stage('unit testing')
            {
                steps{
                    sh 'mvn test'
                }
            }
            stage('deploy to tomcat')
            {
                steps{
                    sh 'mvn package'
                    sshagent(['tomcat']) {
                        sh """
                        scp -o StrictHostKeyChecking=no **/*.war ubuntu@172.31.45.203:/opt/tomcat/apache-tomcat-9.0.33/webapps
                        """
                    }
                }
            }
    }
}