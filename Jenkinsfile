pipeline {
      agent any
      stages {
            stage('clean the  project ') {
                  steps {
                    sh 'mvn clean'
                  }
            }
            stage("Start test execution")
            {
                steps{
                    sh 'mvn test'
                }
            }
             stage("Start test execution"){
                           steps{
                                sh 'mvn package'
                            }
                 }
      }


}