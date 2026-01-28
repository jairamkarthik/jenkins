pipeline {
    agent any

    tools {
        jdk 'Java17'
        maven 'Maven'
    }

    stages {

        stage('Checkout Code') {
            steps {
                echo "Pulling from GITHUB repository"
                git branch: 'main',
                    credentialsId: 'github',
                    url: 'https://github.com/jairamkarthik/jenkins.git'
            }
        }

        stage('Build Project') {
            steps {
                echo "Building my JAVA project"
                dir('mvnproject') {
                    bat 'mvn clean package'
                }
            }
        }

        stage('Test The Appln') {
            steps {
                echo "Testing my JAVA project"
                dir('mvnproject') {
                    bat 'mvn test'
                }
            }
        }

        stage('Deploy the project') {
            steps {
                echo "Project is getting Deployed"
            }
        }
    }

    post {
        success {
            echo 'I succeeded!'
        }
        failure {
            echo 'Failed........'
        }
    }
}