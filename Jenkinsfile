pipeline {
   agent any
   stages {
      stage('ping all ntpclients') {
        steps {
            sh 'sshpass -p \'password\' ssh ansible@prdx-ansible11 "ansible ntpclient -m ping"'
        }
      } 
      stage('check DB servers') {
        steps {
            sh 'sshpass -p \'password\' ssh ansible@prdx-ansible11 "ansible database -m ping"'
        }
      }  
      stage('Check jenkins') {
        steps {
            sh 'sshpass -p \'password\' ssh ansible@prdx-ansible11 "ansible jenkins -m ping"'
        }
      }  
      stage('Ping nfs server connection') {
        steps {
            sh 'sshpass -p \'password\' ssh ansible@prdx-ansible11 "ansible nfs -m ping"'
        }
      }  
    }
}      
