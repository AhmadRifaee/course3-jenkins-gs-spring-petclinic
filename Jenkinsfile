pipeline {
    agent any
    
    stages{
        stage ("checkout") {
            steps{
                git branch: 'main', url: 'https://github.com/AhmadRifaee/course3-jenkins-gs-spring-petclinic.git'
            }
        }
        
        stage ("build") {
            steps{
                sh "./mvnw package"
            }
        }
        
        stage("capture") {
            steps{
                archiveArtifacts artifacts: '**/target/*.jar'
                junit '**/target/surefire-reports/TEST*.xml'
                jacoco()
            }
        }
    }
    
    post {
        always {
            echo "${currentBuild.currentResult}: job ${env.JOB_NAME} [${env.BUILD_NUMBER}]"
        }
    }
}
