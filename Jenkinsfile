node {
   def mvnHome


   	stage('Preparation') { // for display purposes
      	// Get code from a GitHub repository
	git branch: 'mvc_rest', credentialsId: 'xxx', 
		url: 'https://github.com/kvvchetty/springframework.git'
      	// Get the Maven tool.
      	// ** NOTE: This 'maven_3.3.9' Maven tool must be configured
      	// **       in the global configuration.           
      	mvnHome = tool 'maven_3.3.9'

   	}
   	stage('Build') {
      	// Run the maven build
      	if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      	} else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      	}
   	}
   	stage('Results') {
      	junit '**/target/surefire-reports/TEST-*.xml'
      	archive 'target/*.jar'
   	}

}
