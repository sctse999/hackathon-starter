node {
    stage('Example') {

        println env.BRANCH_NAME

        sh "git rev-parse HEAD > .git/commit-id"
                def commit_id = readFile('.git/commit-id').trim()
                println commit_id
                println ${env.version}
                def app = docker.build "hackathon"

    }
}
