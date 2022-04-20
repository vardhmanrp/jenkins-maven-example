pipeline {
    agent any
    environment {
        NEXUS_CREDS = credentials('nexus-deployer')
        NEXUS_USER = "$NEXUS_CREDS_USR"
        NEXUS_PASSWORD = "$NEXUS_CREDS_PSW"
      }
    tools{
        maven "M3"
    }
    stages {
        stage ('Compile Stage') {

            steps {
                
                    sh 'mvn -s settings.xml clean compile'
                
            }
        }

        stage ('Testing Stage') {

            steps {
                
                    sh 'mvn -s settings.xml test'
                
            }
        }


        stage ('Deployment Stage') {
            steps {
                
                    sh 'mvn -s settings.xml deploy -DrepositoryId=releases'
                
            }
        }
    }
}
