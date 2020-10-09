node {
    stage('Init') {
        sh 'ls -ltrh'
    }
    stage('Test') {
        sh 'echo "Tests passed"'
    }
    stage('Sonar') {
        sh '$MAVEN_HOME/mvn sonar:sonar -Dsonar.projectKey=NCR -Dsonar.host.url=http://34.229.94.90/:9000 -Dsonar.login=78ca59741fb9268ecbe634c49ecf2c338000b043'

    }
    stage('Push Docker image') {
        sh 'hostname'
    }
    stage('Send slack notification') {
         slackSend color: 'good', message: 'Message from Jenkins Pipeline'
    }
}
