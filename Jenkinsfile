pipeline{
  agent any
 stages {
stage (pull)
{
    steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'git', url: 'https://github.com/nourhr/angularapp.git']]])
    }
}
stage (build)
{
    steps {
        script{
         sh "sudo ansible-playbook /home/elnb/nour/ansible/build.yaml -i /home/elnb/nour/ansible/host.yaml"
         
        }
    }}
 stage (docker)
{
    steps {
        script{
         sh "sudo ansible-playbook /home/elnb/nour/ansible/docker.yaml -i /home/elnb/nour/ansible/host.yaml"
         
        }
    script{
         sh "sudo ansible-playbook /home/elnb/nour/ansible/docker_reg.yaml -i /home/elnb/nour/ansible/host.yaml"
         
        }    
    }}
    
    
    
 }
    
}
