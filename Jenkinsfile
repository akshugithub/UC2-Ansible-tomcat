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
               sh 'ansible-playbook tomcat_deploy.yaml'
            }
        }
    }
}
