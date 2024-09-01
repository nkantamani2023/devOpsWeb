pipeline{
    agent any
    tools{
        maven 'Maven 3.9.9'
    }
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving artifacts"
                    archiveArtifacts artifact: '**/target/*.war'
                }
            }
        }
        stage('Deploy to tomcat server'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat-server', path: '', url: 'http://13.201.97.38:8080/')], contextPath: null, war: '**/*.war'
            }

        }
    }
}