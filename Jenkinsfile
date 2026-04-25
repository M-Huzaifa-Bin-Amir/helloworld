pipeline {
    agent any

    // Defining tools ensures the required binaries are in the PATH

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

post {
    always {
        echo 'Post Build condition running ...'
    }
        faliur{
            echo'Post Build Faliur Running ...'
        }
    }

        
