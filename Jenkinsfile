pipeline {
    agent any

    environment{
        NEW_VERSION = '1.3.0'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                // Execute shell commands using the 'sh' step
                // sh 'mvn clean package' 
                echo "Building version ${NEW_VERSION}"
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


        
