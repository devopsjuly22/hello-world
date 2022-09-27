pipeline {
	agent { node { label 'jenkins_slave3' } }
	stages {
	    stage ('CleanWorkspace') {
	        steps {
	            cleanWs()
	        }
	    }
		stage ("git-clone") {
			steps {
				sh "git clone https://github.com/ValaxyTech/hello-world.git"
			}
		}
		stage ("build-step") {
			steps {
				sh "mvn -f /home/ec2-user/workspace/pipeline/hello-world/pom.xml clean install"
			}
		}
		stage ("deploy") {
			steps {
				sh "rm /home/ec2-user/tomcat-9/webapps/webapp.war"
				sh "cp /home/ec2-user/workspace/pipeline/hello-world/webapp/target/webapp.war /home/ec2-user/tomcat-9/webapps/"
			}
		}
	}
	
}
