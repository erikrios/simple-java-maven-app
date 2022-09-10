node {
  stage('Build') {
    def mavenImage = docker.image("maven:3-alpine")

    mavenImage.inside('-v /root/.m2:/root/.m2', {
      sh "mvn -B -DskipTests clean package"
    })
  }

  stage('Test') {
    def mavenImage = docker.image("maven:3-alpine")

    mavenImage.inside('-v /root/.m2:/root/.m2', {
      sh "mvn test"
    })
  }
}
