pipeline {
    agent any
    environment {
        JAVA_HOME = '/usr/bin'
        PYTHON_HOME = 'C:\\Users\\rehou\\AppData\\Local\\Programs\\Python\\Python39'
        PATH = "${env.PATH}:${JAVA_HOME}:${PYTHON_HOME}"
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/haythem-rehouma/hello-python-linux.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'echo "Running on Unix"'
                        sh 'javac HelloWorld.java'
                        sh 'java HelloWorld'
                        sh 'python3 hello.py'
                    } else {
                        bat 'echo "Running on Windows"'
                        bat 'javac HelloWorld.java'
                        bat 'java HelloWorld'
                        bat 'python hello.py'
                    }
                }
            }
        }
    }
}
