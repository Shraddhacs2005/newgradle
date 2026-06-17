pipeline {
agent any // Use any available agent
  tools {
    gradle 'Gradle' // Ensure this matches the name configured in Jenkins
    jdk 'jdk'
  }
  stages {
    stage('Build') {
      steps {
        sh 'chmod +x gradlew'
        sh './gradlew build -x test' 
      }
    }
    stage('Test') {
      steps {
        sh './gradlew test' 
      }
  }
  stage('Run Application') {
    steps {
// Start the JAR application
      sh './gradlew assemble'
    }
  }
}
post {
  success {
    echo 'Build and deployment successful!'
  }
  failure {
    echo 'Build failed!'
  }
}
}
