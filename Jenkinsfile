node("agent") {
  def mavenImage = docker.image("maven:3-alpine")

  stage('Build') {
    mavenImage.inside('-v /root/.m2:/root/.m2', {
      sh "pwd"
      sh "ls -al"
      sh "mvn -B -DskipTests clean package"
    })
  }

  stage('Test') {
    mavenImage.inside('-v /root/.m2:/root/.m2', {
      sh "mvn test"
    })
  }
}
