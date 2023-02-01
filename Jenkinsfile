pipeline {
    agent any
    tools { 
        maven 'maven' 
        
           }

    stages {
      stage('GIT checkout') {
           steps {
                git branch: 'main', url: 'https://github.com/akshugithub/UC2-Ansible-tomcat.git'
            }
        }
		stage('build') {
            steps {
               sh 'mvn clean package'
            }
        }
		stage('deploy') {
            steps {
               //sh 'ansible-playbook tomcat_deploy.yaml'
	       //ansiblePlaybook disableHostKeyChecking: true, installation: 'ansible', inventory: 'inventory.yaml', playbook: 'tomcat_deploy.yaml'
	       ansiblePlaybook credentialsId: 'tomcat-creds', disableHostKeyChecking: true, installation: 'ansible', inventory: 'inventory.yaml', playbook: 'tomcat_deploy.yaml'	    
            }
        }
	         stage('SonarQube analysis') {
            steps{
                 withSonarQubeEnv('uc2-sonarqube') { 
                 sh "mvn sonar:sonar"
	}
		}
		}
    }
}
