pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'Maven') {
                    sh 'mvn install package'
                }
            }
        }

        
        
        stage ('Deploy To Tomcat') {
            steps {
                sshagent(['tomcat-ssh']) {
                    sh 'scp /var/lib/jenkins/workspace/first-pipeline/target/rest-hateoas-0.0.1-SNAPSHOT.war /home/ec2-user/apache-tomcat-8.5.32/webapps/'
                }
            }    
        }
        
    }
}
