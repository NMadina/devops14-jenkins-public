pipeline {
   agent any
   stages {
      stage('ssh and run') {
        steps {
            sh 'sshpass -p \'password\' ssh ansible@prdx-ansible11 "ansible all -m ping"'
        }
      }  
    }
}      
