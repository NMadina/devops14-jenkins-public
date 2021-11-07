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
      stage('SSH to ansible and run ping-pong module to all hosts') {
         steps {
            sh "echo pwd"
            sh 'ssh -t -t ansible@prdx-ansible11 -o StrictHostKeyChecking=no "echo pwd && ansible all -m ping"'
         }
      }
   }
}
