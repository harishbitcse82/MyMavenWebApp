pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', 'https://github.com/harishbitcse82/MyMavenWebApp.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }
        stage('Deploy') {
            steps {
                ansiblePlaybook playbook: 'ansible/deploy.yml', inventory: 'ansible/hosts.ini'
            }
        }
    }
}
