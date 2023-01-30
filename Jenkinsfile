pipeline {
    agent {
    label ('ansible')
    }

    stages {
        stage('scm') {
            steps {
               git '<SCM>'
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
