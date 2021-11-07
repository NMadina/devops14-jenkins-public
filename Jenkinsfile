pipeline {
   stages {
      stage('ssh and run') {
         node {
            sh 'sshpass -p \'password\' ssh ansible@prdx-ansible11 "ansible all -m ping"'
         }
      }
   }
}      
