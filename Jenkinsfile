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
        stage ('Build Stage') {
            steps {
               withMaven(maven : 'Maven 3.6.0') {
                   sh 'mvn clean build'
               }
            }
        }
        stage ('Deploy Stage') {
            steps {
               withMaven(maven : 'Maven 3.6.0') {
                   sh 'mvn clean deploy'
               }
            }
        }
    }
}
