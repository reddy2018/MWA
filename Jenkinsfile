node
{
	stage('SCM Checkout')
	{
		git 'https://github.com/Manoha1g/mvn_shoppingcart.git'
	}
	stage('Compile-Package'){
		// Get maven home path
      		def mvnHome =  tool name: 'maven 3.5.4', type: 'maven'   
     		sh "${mvnHome}/bin/mvn package"
	}
	stage('Deploye to tomcat')
	{
		sh '''
		echo deploy the war to tomcat server.

		echo step-1: Removing the existing package 
		rm -rf /home/ec2-user/tomcat/apache-tomcat-9.0.10/webapps/SH*.war

		echo step2: Stagging the new package to tomcat server.
		cp  ${WORKSPACE}/target/*.war /home/ec2-user/tomcat/apache-tomcat-9.0.10/webapps/
		'''
	}
}
