
pipeline{
	agent any
      stages{
           stage('Checkout'){
	    
               steps{
		 echo 'cloning..'
                 git 'https://github.com/Sonal0409/DevOpsClassCodes.git'
              }
          }
          stage('Compile'){
             
              steps{
                  echo 'compiling..'
                  sh 'mvn compile'
	      }
          }
          stage('CodeReview'){
		  
              steps{
		    
		  echo 'codeReview'
                  sh 'mvn pmd:pmd'
              }
          }
           stage('UnitTest'){
		  
              steps{
	         echo 'Testing'
                  sh 'mvn test'
              }
               post {
               success {
                   junit 'target/surefire-reports/*.xml'
               }
           }	
          }
           
          stage('Package'){
		  
              steps{
		  
                  sh 'mvn package'
              }
          }

	      stage("deployment on tomcat"){
steps{

sh "sudo mv /var/lib/jenkins/workspace/akshat-pipeline/target/addressbook.war /opt/apache-
tomcat-8.5.100/webapps/"

}
}
	     
          
      }
}
