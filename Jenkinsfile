pipeline {
    agent any

    tools {
        maven 'Maven' // Ensure this version is configured in Jenkins
        jdk 'Java'      // Ensure this JDK version is configured in Jenkins
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from SCM
                checkout([$class: 'GitSCM',
                        branches: [[name: 'main']],
                        userRemoteConfigs: [[url: 'https://github.com/Megharani2525/jenkins-java-maven-pipeline.git',
                        credentialsId: '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']]])
            }
        }

        stage('Build') {
            steps {
                // Build the project using Maven
                sh 'mvn clean install -DskipTests -q'
            }
        }

        stage('Test') {
            steps {
                // Run unit tests
                // sh 'mvn test'
                sh 'echo "---------Skipping Test-----------"'
            }
        }

        stage('Package') {
            steps {
                // Package the application
                sh 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                // Simple deployment example
                sh 'echo ".....Deploying application...."'
                // Example of copying artifacts to a deploy location
                // sh 'cp target/basic-java-app-1.0-SNAPSHOT.jar /path/to/deploy/'
                //sh 'mvn deploy'
            }
        }
    }

    post {
        always {
            // Clean up actions
            sh 'echo "Cleaning up..."'
        }

        success {
            // Actions on successful build
            echo 'Build succeeded!'
        }

        failure {
            // Actions on failed build
            echo 'Build failed!'
        }
    }
}
