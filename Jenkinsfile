pipeline {
  agent {label 'git-jdk'}
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
