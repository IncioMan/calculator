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
}
