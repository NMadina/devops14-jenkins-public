pipeline {
   agent any
   stages {
      stage('ping ntp client') {
        steps {
            sh 'sshpass -p \'password\' ssh ansible@prdx-ansible11 "ansible ntp -m ping -i ntp_inv"'
        }
      } 
      stage('check DB servers') {
        steps {
            sh 'sshpass -p \'password\' ssh ansible@prdx-ansible11 "ansible database -m ping -i ntp_inv"'
        }
      }  
      stage('Check jenkins') {
        steps {
            sh 'sshpass -p \'password\' ssh ansible@prdx-ansible11 "ansible jenkins -m ping -i ntp_inv"'
        }
      }  
      stage('Check ftp') {
        steps {
            sh 'sshpass -p \'password\' ssh ansible@prdx-ansible11 "ansible ftp -m ping -i ntp_inv"'
        }
      }  
    }
}      
