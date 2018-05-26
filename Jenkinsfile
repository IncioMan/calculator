pipeline {
  agent {label 'git-jdk'}
  triggers {
    pollSCM('* * * * *')
  } 
  stages {
    stage("Compile") {
      steps {
        sh "./gradlew compileJava"
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
      subject: "COmpleted Pipeline: ${currentBuild.fullDisplayName}",
      body: "Your build completed, please check: ${env.BUILD_URL}"
    }
  }
}
