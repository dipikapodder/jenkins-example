pipeline {
    agent any

    tools { 
        maven 'maven3.5.4' 
        jdk 'JDK10' 
    }
    
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }
    
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven3.5.4') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven3.5.4') {
                    sh 'mvn test'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'maven3.5.4') {
                    sh 'mvn deploy'
                }
            }
        }
    }
}
