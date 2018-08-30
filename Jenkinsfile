pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn compile'
                }
            }
        }

        stages {
        stage ('Test Stage') {

            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn test'
                }
            }
        }
            
        stages {
        stage ('Package Stage') {

            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn package'
                }
            }
        }    
        
        
        stage ('Deploy To Tomcat') {
            steps {
                sshagent(['tomcat-ssh']) {
                    sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/first-pipeline/target/rest-hateoas-0.0.1-SNAPSHOT.war ec2-user@ec2-54-154-43-118.eu-west-1.compute.amazonaws.com:/home/ec2-user/apache-tomcat-8.5.32/webapps/'
                }
            }    
        }
        
    }
}
