pipeline {
   agent any
   stages {
      stage('make pizza') {
         steps {
            sh 'rm -rf mypizza'
            sh 'mkdir mypizza'
            sh 'touch pizza/pizza.txt'
            sh 'echo "cheese" >> pizza/pizza.txt'
            sh 'echo "veggie" >> pizza/pizza.txt'
            sh 'echo "chicken" >> pizza/pizza.txt'
         }
      }
      stage('Test') {
          steps {
              sh 'test -f pizza/pizza.txt'
              sh 'grep "cheese" pizza/pizza.txt'
              sh 'grep "veggie" pizza/pizza.txt'
              sh 'grep "chicken" pizza/pizza.txt'
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
