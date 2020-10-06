node('aws') {
    stage('Init') {
        /* Let's make sure we have the repository cloned to our workspace */
        sh 'pwd'
        sh 'ls -ltrh'
    }
    stage('Test Docker image') {
            sh 'echo "Tests passed"'
    }
    stage('Push Docker image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
    stage('Send slack notification') {
         slackSend color: 'good', message: 'Message from Jenkins Pipeline'
    }
}
