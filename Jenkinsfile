node {
    def app;
    checkout scm

    stage('Build image') {
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
        println env.version
        app = docker.build "proactivehk/hackathon"
    }

    stage('Publish image') {
        docker.withRegistry('https://registry.hub.docker.com', 'docker_hub') {
            app.push 'master'
            app.push "${commit_id}"
        }
    }

    stage('Deploy') {
        sh "docker service ls"
    }
}
