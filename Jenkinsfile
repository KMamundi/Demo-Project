pipeline {
   agent any
   stages {
    stage('Main Stage'){
     steps{
        script{
            stage('Remote SSH') {
               withCredentials([file(credentialsId: 'KeyFile', variable: 'KeyFile')]) {
                  // some block
                  def remote = [:]
                  remote.name = 'AWS APAC LG'
                  remote.host = '10.215.3.231'
                  remote.user = 'ec2-user'
                  remote.identityFile = '$KeyFile'
                  remote.allowAnyHosts = true
                  sshCommand remote: remote, command: "ls -lrt"
                  sshCommand remote: remote, command: "for i in {1..5}; do echo -n \"Loop \$i \"; date ; sleep 1; done"
               }
            }   
        }
     }    
    }  
   }
}
