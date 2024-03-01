pipeline {
    agent {
        node {
            label 'maven'
        }
    }
    environment {
        PATH = "/opt/apache-maven-3.9.6/bin:$PATH"
    }

    stages {
        stage('build') {
            steps {
                sh 'mvn clean deploy'
            }
        }
    stage ('sonarqubeanalysis') {
        environment {
           scannerHome = tool 'dev-sonar-scanner'
        }
    steps{
       withSonarQubeEnv('sonar-server'){
      sh "${scannerHome}/bin/sonar-scanner"
       }
      } 
    }
  }
}

