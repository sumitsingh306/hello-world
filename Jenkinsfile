pipeline {
    agent any
    tools { 
        maven 'Maven 3.6.0' 
        jdk 'java-1.8.0-openjdk-amd64' 
    }
    stages {
        stage ('Initialize Maven') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }

        stage ('Build') {
            environment  {
                MVN_COMMAND = "mvn clean package"
                TEST_REPORTS = "target/surefire-reports/*.xml"
            }
        }
    }
}
