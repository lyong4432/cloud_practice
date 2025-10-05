node {
    def app
    stage('Clone repository') {
        git 'https://github.com/lyong4432/cloud_practice.git'
    }
    stage('Build image') {
        app = docker.build("pjbear/test")
    }
    stage('Test image') {
        app.inside {
            sh 'make test'
        }
    }
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
           app.push("${env.BUILD_NUMBER}")
           app.push("latest")
        }
    }
}
