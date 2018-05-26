pipeline {
  agent {label 'git-jdk-docker'}
  triggers {
    pollSCM('* * * * *')
  } 
  stages {
    stage("Package") {
      steps {
        //sleep 600
        sh "./gradlew build"
       }
     }
     stage("Docker build") {
      steps {
        sh "docker build -t registry:5000/calculator ."
       }
     }
     stage("Docker push") {
      steps {
        sh "docker push registry:5000/calulcator"
       }
     }
     stage("Unit test") {
       steps {
         sh "./gradlew test"
       }
     }
  }
  post {
    always {
      mail to: 'alex.incerti@outlook.com',
      subject: "Completed Pipeline: ${currentBuild.fullDisplayName}",
      body: "Your build completed, please check: ${env.BUILD_URL}"
    }
  }
}
