node {

  try {
  
  stage('Code Checkout') { 
      // Get some code from a GitHub repository
      git 'https://github.com/amanpahal/calcwebapp.git'

   }
   
   stage('Unit Test') { 
      // Get some code from a GitHub repository
      sh("mvn test")

   }
   
   stage('Test Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
   
   stage('Package & Deploy') {
   sh("mvn package")
	 /bin/sh 'curl --upload-file target/aman.war "http://deployer:deployer@6243cfba.ngrok.io:8081/manager/text/deploy?path=aman&update=true"'
   }
   

} 
catch(e) {
	echo "Caught some exception"
	
    mail bcc: '', body: '''Jenkins build Failure!!!
	
    Better get it fixed
    Anand''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'anandr72@gmail.com' 
}  finally {
	echo "Finally Block"
	
	mail bcc: '', body: '''Jenkins build Success!!
	
    Build executed!
    Anand''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'anandr72@gmail.com' 

}
    
}
