node('Jenkins-VM') {
  stage('Build') {
    def mavenImage = docker.image("maven:3-alpine")

    mavenImage.inside {
      sh "mvn -B -DskipTests clean package"
    }
  }

  stage('Test') {
    def mavenImage = docker.image("maven:3-alpine")

    mavenImage.inside {
      sh "mvn test"
    }
  }
}
