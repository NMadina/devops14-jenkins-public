pipeline {
   agent any
   def remote = [:]
   remote.name = "node"
   remote.host = "prdx-ansible11"
   remote.allowAnyHosts = true
   
   stages {
      stage("set env") 
        node {
         withCredentials([usernamePassword(credentialsId: 'sshUserAcct', passwordVariable: 'password', usernameVariable: 'userName')]) {
         remote.user = ansible
         remote.password = password

       stage("SSH Steps Rocks!") {
           sshCommand remote: remote, command: 'echo pwd && ansible all -m ping'
       }
      }
}
      
   }
}
