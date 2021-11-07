pipeline {
   agent any
   stages {
      stage('make pizza') {
         steps {
            sh 'rm -rf mypizza'
            sh 'mkdir mypizza'
            sh 'touch mypizza/pizza.txt'
            sh 'echo "cheese" >> mypizza/pizza.txt'
            sh 'echo "veggie" >> mypizza/pizza.txt'
            sh 'echo "chicken" >> mypizza/pizza.txt'
         }
      }
      stage('Test') {
          steps {
              sh 'test -f mypizza/pizza.txt'
              sh 'grep "cheese" mypizza/pizza.txt'
              sh 'grep "veggie" mypizza/pizza.txt'
              sh 'grep "chicken" mypizza/pizza.txt'
          }
      }

def remote = [:]
remote.name = "node"
remote.host = "prdx-ansible11"
remote.allowAnyHosts = true

node {
    withCredentials([usernamePassword(credentialsId: 'sshUserAcct', passwordVariable: 'password', usernameVariable: 'userName')]) {
        remote.user = ansible
        remote.password = password

        stage("SSH Steps Rocks!") {
            sshCommand remote: remote, command: 'echo pwd && ansible all -m ping'

        }
    }
}
      
   }
}
