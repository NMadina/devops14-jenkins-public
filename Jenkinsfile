pipeline {
   agent any
   stages{
      stage('SSH to ansible and run ping-pong module to all hosts') {
       steps {
           sh 'ssh -t -t ansible@prdx-ansible11 -o StrictHostKeyChecking=no "echo pwd && ansible all -m ping"'
       }
      }
      stage('ping ntpserver') {
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
      stage('Ping nfs server connection') {
        steps {
            sh 'sshpass -p \'password\' ssh ansible@prdx-ansible11 "ansible nfs -m ping -i ntp_inv"'
        }
      }  
    }
}      
