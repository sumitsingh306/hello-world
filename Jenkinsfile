pipeline {
   /* stanza for simple maven pipeline */
    agent any
    tools { 
        maven 'Maven 3.6.0' 
        jdk 'jdk8' 
    }
    stages {
        stage ('Compile Stage') {
            steps {
                withMaven(maven : 'Maven 3.6.0') {
                    sh 'mvn clean compile'
                }
            }
        }
        stage ('Testing Stage') {
            steps {
               withMaven(maven : 'Maven 3.6.0') {
                   sh 'mvn clean test'
               }
            }
        }
        stage ('Packaging Stage') {
            steps {
               withMaven(maven : 'Maven 3.6.0') {
                   sh 'mvn clean package'
               }
            }
        }
        stage ('Install Stage') {
            steps {
               withMaven(maven : 'Maven 3.6.0') {
                   sh 'mvn clean install'
               }
            }
        }
       stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonarqube-8.2.0.32929') {
                    // Optionally use a Maven environment you've configured already
                    withMaven(maven:'Maven 3.6.0') {
                        sh 'mvn clean verify sonar:sonar'
                    }
                }
            }
        }
        stage("Quality Gate") {
            steps {
                timeout(time: 1, unit: 'MINUTES') {
                    // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                    // true = set pipeline to UNSTABLE, false = don't
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}   
