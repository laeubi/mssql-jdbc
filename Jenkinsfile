pipeline {
    agent any
    tools { 
        jdk 'JDK9' 
    }
    stages {
       	stage('checkout') {
		steps {
	            git url: 'https://github.com/laeubi/mssql-jdbc.git', branch: 'lablicate'
			}
        }
        stage ('Build') {
            steps {
                sh 'mvn -B -Dmaven.repo.local=.repository -Pbuild42 -DskipTests clean install'
                sh 'mvn -B -Dmaven.repo.local=.repository -f updateSite/pom.xml clean install'
            }
        }
		stage ('archive') {
			steps {
			      archiveArtifacts '**/target/*.jar'
			}
		}
    }
}
