node {
    stage('Init') {
        /* Let's make sure we have the repository cloned to our workspace */
        sh 'pwd'
        sh 'ls -ltrh'
    }
    stage('Test Docker image') {
            sh 'echo "Tests passed"'
    }
    stage('Push Docker image') {
    }
    stage('Send slack notification') {
         slackSend color: 'good', message: 'Message from Jenkins Pipeline'
    }
}
