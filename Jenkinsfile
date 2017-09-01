pipeline {
    // agent { dockerfile true }

    stage('Image') {
        sh "git rev-parse HEAD > .git/commit-id"
         def commit_id = readFile('.git/commit-id').trim()
        println commit_id
        println ${env.version}
       def app = docker.build "hackathon"

    }

}