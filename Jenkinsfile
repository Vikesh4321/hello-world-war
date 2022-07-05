pipeline {
    agent any
    environment {
        PATH="/opt/apache-maven-3.8.6/bin/:$PATH"
        PATHH="/opt/apache-tomcat-9.0.64/bin/:$PATHH"
    }

    stages {
        stage('fetch') {
            steps {
               // echo 'Hello World'
               git 'https://github.com/Vikesh4321/hello-world-war.git'
            }
        }
        stage('BUILD') {
            steps {
               // echo 'Hello World'
               //git 'https://github.com/Vikesh4321/hello-world-war.git'
               sh "mvn clean package"
            }
        }
        stage('Deploy') {
            steps {
               // echo 'Hello World'
               //git 'https://github.com/Vikesh4321/hello-world-war.git'
               deploy adapters: [tomcat9(credentialsId: 'tomcat_creden', path: '', url: 'http://54.235.8.10:8888/')], contextPath: null, onFailure: false, war: '**/*.war'
            }
        }
    }
}

