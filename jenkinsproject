pipeline {
    agent any
    stages {
        stage ('Checkout') {
            steps {
                    git branch: 'main', url: 'git@github.com:Vakhob/devops14-jenkins-public.git'
                }
            }

        stage ('Test') {
            steps {
                script{
                    sh "chmod +x -R ${env.WORKSPACE}/../${env.JOB_NAME}/pipeline.sh"
                }
            }
        }
    }
}
