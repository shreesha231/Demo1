pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out frontend project...'
                checkout scm
            }
        }

        stage('Verify Files') {
            steps {
                echo 'Checking frontend files...'

                bat 'dir'

                bat 'if not exist index.html exit 1'
                bat 'if not exist index.css exit 1'
                bat 'if not exist index.js exit 1'

                echo 'All frontend files are present!'
            }
        }

        stage('Build') {
            steps {
                echo 'Building frontend project...'
                echo 'No compilation required for this simple HTML/CSS/JS project.'
            }
        }

        stage('Archive') {
            steps {
                echo 'Archiving frontend files...'

                archiveArtifacts artifacts: 'index.html,index.css,index.js',
                                 fingerprint: true
            }
        }

    }

    post {

        success {
            echo 'Frontend Jenkins pipeline completed successfully!'
        }

        failure {
            echo 'Frontend Jenkins pipeline failed!'
        }

    }
}
