pipeline {
    agent any

    environment {
        // Java 21 sur ta VM - commande readlink -f $(which java) va donner /usr/lib/jvm/java-21-openjdk-amd64/bin/java donc  JAVA_HOME   = '/usr/lib/jvm/java-21-openjdk-amd64'
        JAVA_HOME   = '/usr/lib/jvm/java-21-openjdk-amd64'
        // Python sera dans /usr/bin (python3) - commande which python3 ==> /usr/bin/python3 donc PYTHON_HOME = '/usr/bin'
        PYTHON_HOME = '/usr/bin'
        PATH = "${env.PATH}:${JAVA_HOME}/bin:${PYTHON_HOME}"
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
                        // Java (si tu as un HelloWorld.java dans le repo)
                        sh 'javac HelloWorld.java'
                        sh 'java HelloWorld'
                        // sinon  uniquemnet une seule commande sh 'java HelloWorld.java'

                        // Python
                        sh 'python3 --version'
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
