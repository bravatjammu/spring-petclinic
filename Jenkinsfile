pipeline {
    agent any
    triggers{
        // Triggers pipeline for every commit on git repo
        pollSCM '* * * * *'
    }
   
    stages {
        stage('Stage 1'){
        agent {
            label 'rishi12'
        }
        steps {
            // Get some code from a GitHub repository
            git branch: 'main', credentialsId: 'nrajulearning', url: 'https://github.com/bravatjammu/spring-petclinic.git'
            // Run Maven on a Unix agent.
            sh "mvn clean package"

            }
        }

    }
        post{
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
}
