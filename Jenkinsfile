pipeline {

    agent any
 
    stages {
        // Stage 1: Checkout code from Git
        stage('Checkout') {
            steps {
                // Fetch the code from the Git repository
                git branch: 'main', // Replace with your branch name (e.g., 'master', 'develop')
                    credentialsId: '3d155c11-794a-4d56-b9b3-d46fccd770ba', // Replace with your Jenkins credentials ID
                    url: 'https://github.com/Jagdish-cloud/maven_cont.git' // Replace with your Git repo URL
            }
        }

        // Stage 2: Build the Maven project
        stage('Build') {
            steps {
                // Use 'bat' for Windows batch commands instead of 'sh' (Unix shell)
                bat 'mvn clean install'
            }
        }

        // Optional Stage 3: Archive the build artifacts
        stage('Archive Artifacts') {
            steps {
                // Archive the generated JAR/WAR files (adjust the path as needed)
                archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            }
        }
    }

    // Post-build actions (optional)
    post {
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed. Check the logs for details.'
        }
        always {
            echo 'Pipeline execution finished.'
        }
    }
}
