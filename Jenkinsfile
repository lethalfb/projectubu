
pipeline{
	agent any
      stages{
           stage('Checkout'){
	    
               steps{
		 echo 'cloning..'
                 git 'https://github.com/lethalfb/projectubu.git'
              }
          }
          stage('codecompile'){
             
              steps{
                  echo 'compiling..'
                  sh 'mvn compile'
	      }
          }
          stage('codeQA'){
		  
              steps{
		    
		  echo 'codeReview'
                  sh 'mvn pmd:pmd'
              }
          }
           stage('codetest'){
		  
              steps{
	         
                  sh 'mvn test'
              }
               post {
               success {
                   junit 'target/surefire-reports/*.xml'
               }
           }	
          }
          
          stage('codepackage'){
		  
              steps{
		  
                  sh 'mvn package'
              }
          }
	     
          
      }
}
