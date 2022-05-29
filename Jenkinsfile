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
    }
}
