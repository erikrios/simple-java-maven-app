node {
  stage('Build') {
    def mavenImage = docker.image("maven:3.8.6-eclipse-temurin-11-alpine")

    mavenImage.inside('-v /root/.m2:/root/.m2', {
      sh "mvn -B -DskipTests clean package"
    })
  }

  stage('Test') {
    def mavenImage = docker.image("maven:3.8.6-eclipse-temurin-11-alpine")

    mavenImage.inside('-v /root/.m2:/root/.m2', {
      sh "mvn test"
    })
  }

  stage('Manual Approval') {
    def mavenImage = docker.image("maven:3.8.6-eclipse-temurin-11-alpine")

    mavenImage.inside('-v /root/.m2:/root/.m2', {
      input message: 'Lanjutkan ke tahap Deploy?'
    })
  }

  stage('Deploy') {
    def mavenImage = docker.image("maven:3.8.6-eclipse-temurin-11-alpine")

    mavenImage.inside('-v /root/.m2:/root/.m2', {
      sh './jenkins/scripts/deliver.sh' 
      sh 'sleep 1m'
      sh './jenkins/scripts/kill.sh' 
    })
  }
}
