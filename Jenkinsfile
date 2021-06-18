def remote = [:]
remote.name = 'test'
remote.host = '192.168.1.110'
remote.port = 22
remote.allowAnyHosts = true

pipeline {
  agent any
  stages{
    //stage('Git Clone') {
            //steps {
                // Get some code from a GitHub repository
                //git branch: 'main', credentialsId: 'github', url: 'https://github.com/subhadipdasgit/ssh-k8s-deployment.git'
            //}
        //}
     stage('Deployment'){
        steps {
            script {
             withCredentials([usernamePassword(credentialsId: 'practice-id', passwordVariable: 'pass', usernameVariable: 'user')]) {
             remote.user = user  
             remote.password = pass
             //sshPut remote: remote, from: "deployment.yml", into: "/home/subhadip"
             sshCommand remote: remote, command: "kubectl apply -f deployment.yml"
            }
           }
          }
        }
      }
    }
