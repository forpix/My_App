node{
   stage('SCM Checkout'){
       git credentialsId: 'git-creds', url: 'https://github.com/forpix/My_App/'
   }
   stage('Mvn Package'){
     def mvnHome = tool name: 'maven', type: 'maven'
     def mvnCMD = "${mvnHome}/bin/mvn"
     sh "${mvnCMD} clean package"
     sh "pwd"
     sh 'date'
   }
   stage('Build Docker Image'){
     sh 'docker build -t mdaali/my-app:2.0.0 .'
   }
   stage('Push Docker Image'){
      withCredentials([string(credentialsId: 'docker-pswd', variable: 'dockerpwd')]) {
    // some block
         sh "docker login -u mdaali -p ${dockerpwd}"
}    
     sh 'docker push mdaali/my-app:2.0.0'
   }
   stage('Run Container on Dev Server'){
     sh 'docker run -it --hostname Jenkins_onRow --name Jenkins_onRun ubuntu /bin/bash'
   }
}
