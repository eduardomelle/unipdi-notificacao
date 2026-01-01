pipeline {
    agent any
    tools {
        maven 'Default'
    }
    environment {
        AWS_REGION = 'sa-east-1'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build com Maven') {
            steps {
                // dir('unipdi-notificacao') {
                    // bat 'mvn -B clean package -DskipTests'
                    sh 'mvn -B clean package -DskipTests'
                // }
            }
        }
        stage('Renomear JAR') {
            steps {
                // dir('unipdi-notificacao') {
                    // bat 'ren target\\unipdi*.jar unipdi-notificacao.jar'
                    // sh 'ren target\\unipdi*.jar unipdi-notificacao.jar'
                    sh 'mv target/unipdi-notificacao-1.0-SNAPSHOT.jar unipdi-notificacao.jar'
                // }
            }
        }
        /*stage('Deploy na AWS') {
            steps {
                // dir('unipdi-notificacao') {
                    withCredentials([usernamePassword(credentialsId: 'aws-creds', usernameVariable: 'AWS_ACCESS_KEY_ID', passwordVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                        // bat 'aws lambda update-function-code --function-name unipdi-notificacao --zip-file fileb://target\\\\unipdi-notificacao.jar --publish --region %AWS_REGION%'
                        sh 'aws lambda update-function-code --function-name unipdi-notificacao --zip-file fileb://target\\\\unipdi-notificacao.jar --publish --region %AWS_REGION%'
                    }
                // }
            }
        }*/
    }
}