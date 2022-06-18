pipeline {
    agent any
    triggers { pollSCM('* * * * *') }

    stages {
        //stage('Build') {
            
            // implicit Checkout
            //steps {
                // Get some code from a GitHub repository
                //git 'https://github.com/jglick/simple-maven-project-with-tests.git'                
            //}
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
    }
    // post after stages, for entire pipeline, is also an implicit step albeit with explicit config here, unlike implicit checkout stage
    post {
        always {
            junit '**/target/surefire-reports/TEST-*.xml'
            archiveArtifacts 'target/*.jar'
        }
    }            
}
