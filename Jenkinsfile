pipeline {
    agent {label 'ubuntu20'}

 //   tools {
        // Install the Maven version configured as "M3" and add it to the path.
        // no need since we using a wrapper
 //   }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: 'github-provatekey', url: 'https://github.com/adirgit84/jgsu-spring-petclinic.git'
            }        
        }
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
         post {
                success {
                    always { 
                        junit '**/target/surefire-reports/TEST-*.xml'
                        archiveArtifacts 'target/*.jar'
                    }
                }
            } 
        }
    }
}