node("docker") {
    docker.withRegistry('contardo.acuna@gmail.com', 'docker-hub-credentials') {
    
        git url: "", credentialsId: 'git-hub-credentials'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "Test Jenkins"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
node {

   stage('Clone Repository') {
        // Get some code from a GitHub repository
        git 'https://github.com/ContardoRM/HelloWorldCI'
    
   }
   stage('Build Maven Image') {
        docker.build("maven-build")
   }
   
   stage('Run Maven Container') {
       
        //Remove maven-build-container if it exisits
        sh " docker rm -f maven-build-container"
        
        //Run maven image
        sh "docker run --rm --name maven-build-container maven-build"
   }
   
   stage('Deploy Spring Boot Application') {
        
         //Remove maven-build-container if it exisits
        sh " docker rm -f java-deploy-container"
       
        sh "docker run --name java-deploy-container --volumes-from maven-build-container -d -p 8090:8090 denisdbell/petclinic-deploy"
   }

}
