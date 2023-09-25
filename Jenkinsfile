pipeline {
    agent any
    
    stages{

        stage ("checkout"){
              steps {
               git branch:'main', url: 'https://github.com/zsolt-github/Spring-Petclinic-Clone.git'
//               git branch:'main', url: 'https://github.com/g0t4/course3-jenkins-gs-spring-petclinic.git'
            }    
        }

        stage ("build"){
            steps {    
                sh "./mvnw package"
            }
        }

        stage ("capture"){
            steps {
                archiveArtifacts artifacts: '**/target/*.jar'
                jacoco()
                junit '**/target/surefire-reports/TEST*.xml'
            }
        }
    }
    
//    post{
//        always {
//            emailtext body: "${env.BUILD_URL}\n${currentBuild.absoluteUrl}",
//                to: 'always@myemail.org',
//                recipientProviders: [previous()],
//                subject: "${currentBuild.currentResult}: Job ${env.JOB_NAME [${evn.BUILD_NUMBER}]}"
//        }
//    }        
}