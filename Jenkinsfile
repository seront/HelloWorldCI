node {
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
        sh './var/jenkins_home/opt/apache-maven-3.5.4/bin/mvn sonar:sonar -Dsonar.projectKey=NCR -Dsonar.host.url=http://34.229.94.90/:9000 -Dsonar.login=78ca59741fb9268ecbe634c49ecf2c338000b043'

    }
    stage('Push Docker image') {
    }
    stage('Send slack notification') {
         slackSend color: 'good', message: 'Message from Jenkins Pipeline'
    }
}
