pipeline {
    agent any
    environment {
        NEXUS_CREDS = credentials('NexusArtifactoryLogin')
        NEXUS_USER = "$NEXUS_CREDS_USR"
        NEXUS_PASSWORD = "$NEXUS_CREDS_PSW"
      }
    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn -s settings.xml clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn -s settings.xml test'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn -s settings.xml deploy'
                }
            }
        }
    }
}
