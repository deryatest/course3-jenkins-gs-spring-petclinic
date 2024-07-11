pipeline {
    agent any
    
    stages{
        stage("checkout"){
            steps {
                git branch: 'main', url: 'https://github.com/deryatest/course3-jenkins-gs-spring-petclinic'
            }
        }
        stage("build"){
            steps {
                bat "./mvnw.cmd package"
            }
        }

        stage("capture"){
            steps {
             archiveArtifacts artifacts: '**/target/*.jar', followSymlinks: false
            jacoco()
            junit stdioRetention: '', testResults: '**/target/surefire-reports/TEST*.xml'   
            }
        }
    }
}
