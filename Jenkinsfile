pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn clean compile'
                }
            }
        }

        
        
        stage ('Deploy To Tomcat') {
            steps {
                sh 'cp /var/lib/jenkins/workspace/second-maven/target/rest-hateoas-0.0.1-SNAPSHOT.war apache-tomcat-8.5.32/webapps/'
            }    
        }
        
    }
}
