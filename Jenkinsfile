pipeline {
    agent any

    stages {
        stage('Pull') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                	userRemoteConfig: [[
                		credentialsId: 'GitHubUsernameAndPassword',
                		url: 'https://github.com/yassine-mechiche-esprit/devops-cd.git'
                	]]
                ])
            }
        }
        stage('Build') {
            steps {
                script{
                	sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
                }
            }
        }
        stage('Docker') {
            steps {
                script{
                	sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml"
                }
            }
        }
        stage('Push to DockerHub') {
            steps {
                script{
                	sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml"
                }
            }
        }
    }
}
