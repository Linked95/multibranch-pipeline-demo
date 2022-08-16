pipeline {

    agent {
        node {
            label 'master'
        }
    }

    options {
        buildDiscarder logRotator( 
                    daysToKeepStr: '14', 
                    numToKeepStr: '20'
            )
    }

    stages {
        
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace For Project"
                """
            }
        }

        stage('Code Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/spring-projects/spring-petclinic.git']]
                ])
            }
        }
        
        stage('Build Code') {
            steps {
                sh """
                echo "Build Code"
                """
            }
        }

        stage('Unit Testing') {
            steps {
                sh """
                echo "Running Unit Tests"
                """
            }
        }
        
        stage('Deploy Test Env') {
            steps {
                sh """
                echo "Deploy Test Env"
                """
            }
            
            steps {
                sh """
                echo "Deploy Test Env Two"
                """
            }
        }

        stage('Code Analysis') {
            steps {
                sh """
                echo "Running Code Analysis"
                """
            }
        }

        stage('Build Deploy Code') {
            when {
                branch 'develop'
            }
            steps {
                sh """
                echo "Building Artifact"
                """

                sh """
                echo "Deploying Code"
                """
            }
        }

    }   
}
