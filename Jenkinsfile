pipeline {
  agent {label 'git-jdk-docker'}
  triggers {
    pollSCM('* * * * *')
  }
  environment{
    REGISTRY = '172.18.0.2'
    IMAGE_NAME = 'calculator'
  }
  stages {
    stage("Package") {
      steps {
        sleep 120
        sh "./gradlew build"
       }
     }
     stage("Docker build") {
      steps {
        sh "docker build -t ${env.REGISTRY}:5000/${env.IMAGE_NAME} ."
       }
     }
     stage("Docker push") {
      steps {
        sh "docker push ${env.REGISTRY}:5000/${env.IMAGE_NAME}" 
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
