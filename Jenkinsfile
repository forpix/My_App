node{
  tools { 
        maven 'Maven Tool'
	}
   
   stage('SCM Checkout'){
     git 'https://github.com/forpix/My_App'
   }
   stage('Compile-Package'){
      sh 'mvn compile'
   }
}
