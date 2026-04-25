pipeline {
    agent any

    // Defining tools ensures the required binaries are in the PATH
    tools {
        // Example: maven 'mvn-3.8.1' or nodejs 'node-16'
        // This is configured under Manage Jenkins > Global Tool Configuration
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                // Execute shell commands using the 'sh' step
                // sh 'mvn clean package' 
            }
        }

        stage('Test') {
            steps {
                echo 'Testing..'
                // sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying....'
                // sh './deploy-script.sh'
            }
        }
    }

    // The post section handles actions based on the build outcome
    post {
        always {
            echo 'Cleaning up workspace...'
            deleteDir() // Removes the build directory to save disk space
        }
        success {
            echo 'Build succeeded.'
        }
        failure {
            echo 'Build failed. Checking logs...'
        }
    }
}
