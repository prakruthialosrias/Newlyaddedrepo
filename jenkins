	pipeline {
		agent any

		       stages {


			        stage('Get the code from the github') {
				      steps { 
					         echo 'Cloning started'
				                 git  'https://github.com/prakruthialosrias/Newaddressbook.git'
					    }}


				stage('Compile') {
				       steps {  
					         echo 'Compiling started'   
				           sh      '/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/mymaven/bin/mvn   compile' 
					   }}


				stage('Test'){
				        steps {  echo 'Testing started'
				             sh    '/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/mymaven/bin/mvn   test'
					  }}
		
				
                                 stage('Package'){
					steps {  echo 'Package started'
				               sh  '/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/mymaven/bin/mvn package'
					  }}
		
	  		         stage('Deploy the code'){
					 steps { echo 'Package started'
   					        sh 'sudo cp /var/lib/jenkins/workspace/AddressBookPackage/target/addressbook.war /usr/share/tomcat/webapps'
					        sh 'sudo systemctl stop tomcat'
					        sh 'sudo rm -rf /usr/share/tomcat/webapps/addressbook'
    					        sh 'sudo systemctl start tomcat'
					    }}
                               }
			}
