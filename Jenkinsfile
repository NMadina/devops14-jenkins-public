pipeline {
   stages {
      node {
         stage 'Does sshpass work?'
         sh 'sshpass -p \'password\' ssh ansible@prdx-ansible11 "ansible all -m ping"'
      }
   }
}
      
