node {
  
  deleteDir()
  stage 'checkout'
      checkout scm
      sh 'echo "uname -a && date" > test.sh'
      sh 'chmod +x *.sh'
  
  
  stage 'build' 
      // no build steps
  
  
  stage 'deploy' 
  
  sshagent (credentials: ['target']) {
        sh 'scp *.sh ubuntu@10.0.0.51:/tmp'
        sh 'ssh -o StrictHostKeyChecking=no -l ubuntu 10.0.0.51 ls -ltr /tmp && ./docker-ce.sh'
        sh 'ssh -o StrictHostKeyChecking=no -l ubuntu 10.0.0.51 docker --version'
     }
  
 
}
