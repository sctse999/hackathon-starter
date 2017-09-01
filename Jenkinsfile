node {
    def app;
    checkout scm

    stage('Build image') {
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
        println env.version
        app = docker.build "hackathon"
    }

    stage('Publish image') {
        app.push 'master'
        app.push "${commit_id}"
    }
}
