pipeline {
    agent any

    stages {
        stage('Build')
        {
            steps
            {
                sh 'mvn clean package'
            }
  
            post
            {
               success
               {
                    echo "Archive the artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
            
               }
        
            }
        }
        stage('Deploy to tomcat server')
        {
            steps
            {
                deploy adapters: [tomcat7(path: '', url: 'http://54.80.242.132:8085/')], contextPath: null, war: '**/*.war'
            }
        }
  
    }

}
