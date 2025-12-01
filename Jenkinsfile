pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                bat 'javac LinkedListDemo.java'
            }
        }
        stage('Run') {
            steps {
                bat 'java LinkedListDemo'
            }
        }
    }
}