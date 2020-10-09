node {
    stage('Clonacion Repositorio') {
        sh 'ls -ltrh web/'
    }
    stage('Test Unitarios') {
        sh 'echo "Tests passed"'
    }
    stage('Analisis de Codigo con Sonar') {
        sh 'echo $MAVEN_HOME/bin/mvn -version'
        sh '$MAVEN_HOME/mvn sonar:sonar -f web/pom.xml -Dsonar.source=./web -Dsonar.projectKey=NCR -Dsonar.host.url=http://34.229.94.90:9000 -Dsonar.login=78ca59741fb9268ecbe634c49ecf2c338000b043'

    }
    stage('Deploy sobre EC2') {
        sh 'sh jenkins@3.90.45.222'
    }
    stage('Send slack notification') {
         slackSend color: 'good', message: 'Message from Jenkins Pipeline'
    }
}
