pipeline {
    agent any
    
    tools {
        // Ensure 'Maven' matches the name defined in Global Tool Configuration
        maven 'Maven'
    }

    parameters {
        string(name: 'DEPLOY_VERSION', defaultValue: '1.0.0', description: 'Version to deploy on prod')
        choice(name: 'TARGET_ENVIRONMENT', choices: ['1.1.0', '1.2.0', '1.3.0'], description: 'Select version')
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Check to run tests')
    }
    
    environment {
        NEW_VERSION = '1.3.0'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                echo "Building version ${env.NEW_VERSION}"
                // Use 'mvn' for Maven commands; 'nvm' is for Node Version Manager
                bash 'mvn install'
            }
        }

        stage('Test') {
            // Conditional execution based on the boolean parameter
            when {
                expression { params.executeTests == true }
            }
            steps {
                echo 'Testing..'
                bat 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying version ${params.DEPLOY_VERSION}...."
                // sh './deploy-script.sh'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up workspace...'
            deleteDir()
        }
        success {
            echo 'Build succeeded.'
        }
        failure {
            echo 'Build failed. Checking logs...'
        }
    }
}
