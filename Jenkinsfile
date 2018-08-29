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
                sshagent(['Tomcat_Credentials']) {
                    sh 'scp /var/lib/jenkins/workspace/second-maven/target/rest-hateoas-0.0.1-SNAPSHOT.war /home/ec2-user/apache-tomcat-8.5.32/webapps/'
                }
            }    
        }
        
    }
}
