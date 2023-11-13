node {
    def app
    stage('Clone repository') {
        git 'https://github.com/choiyoorim/fork_vs_vfork.git'
    }
    stage('Build image') {
        app = docker.build("choiyoorim/test")
    }
    stage('Test image') {
        app.inside {
            sh 'make test'
        }
    }
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'yulim3839') {
           app.push("${env.BUILD_NUMBER}")
           app.push("latest")
        }
    }
}
