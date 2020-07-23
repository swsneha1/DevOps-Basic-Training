pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }

    stages {
        stage('Build') {
            stage('Sonar Scan'){
            steps{
                sh label: '', script: 'mvn clean package sonar:sonar'
            }
        }
            steps {
                // Get some code from a GitHub repository
                git 'https://https://github.com/kmayer10/DevOps-Basics-Batch-4.git'

                // Run Maven on a Unix agent.
                sh "mvn -Dmaven.test.failure.ignore=true clean package"

              
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    //junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.war'
                }
            }
        }
    }
}
