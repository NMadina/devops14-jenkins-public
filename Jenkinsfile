pipeline {
   agent any
   stages {
      stage('ping ntp clients') {
        steps {
            sh 'sshpass -p \'password\' ssh ansible@prdx-ansible11 "ansible ntpclient -m ping -i ntp_inv"'
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
      stage('Check nfs') {
        steps {
            sh 'sshpass -p \'password\' ssh ansible@prdx-ansible11 "ansible nfs -m ping -i ntp_inv"'
        }
      }  
    }
}      
