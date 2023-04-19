pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M2_HOME"
    }

    stages {
        stage('git pull') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/rukesh2devops/addressbook.git'

                // Run Maven on a Unix agent.
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            
            }
		}	
		stage('Deploy to tomcat') {
		    steps {
			    deploy adapters: [tomcat9(credentialsId: 'tomcat-ok', path: '', url: 'http://10.128.0.6:8080')], contextPath: null, war: '**/*.war'
        	}
		}	

                        
   }
}

