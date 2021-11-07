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
            writeFile file: 'test.sh', text: 'ls'
            sshCommand remote: remote, command: 'for i in {1..5}; do echo -n \"Loop \$i \"; date ; sleep 1; done'
            sshScript remote: remote, script: 'test.sh'
            sshPut remote: remote, from: 'test.sh', into: '.'
            sshGet remote: remote, from: 'test.sh', into: 'test_new.sh', override: true
            sshRemove remote: remote, path: 'test.sh'
        }
    }
}
      
   }
}
