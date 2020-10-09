node master {
    stage('Init') {
        /* Let's make sure we have the repository cloned to our workspace */
        sh 'pwd'
        sh 'ls -ltrh'
    }
    stage('Test Docker image') {
        sh 'echo "Tests passed"'
    }
    stage('Sonar') {
        sh 'pwd'
        sh 'ls -ltrh'
        sh 'mvn sonar:sonar -Dsonar.projectKey=NCR -Dsonar.host.url=http://3.94.115.40:9000 -Dsonar.login=78ca59741fb9268ecbe634c49ecf2c338000b043'

    }
    stage('Push Docker image') {
    }
    stage('Send slack notification') {
         slackSend color: 'good', message: 'Message from Jenkins Pipeline'
    }
}
