node{
     
    stage('SCM Checkout'){
        git credentialsId: 'GIT_CREDENTIALS', url:  'https://github.com/chanduej/spring-boot-mongo-docker.git',branch: 'master'
    }
    
    stage(" Maven Clean Package"){
      def mavenHome =  tool name: "maven3", type: "maven"
      def mavenCMD = "${mavenHome}/bin/mvn"
      sh "${mavenCMD} clean package"
      
    } 
    
    
    stage('Build Docker Image'){
        sh 'docker build -t lucky0524/spring-boot-mongo .'
    }
    
    stage('Push Docker Image'){
        withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'King@5559', usernameVariable: 'lucky0524')])
        {
          sh "docker login -u lucky0524 -p King@5559"
        }
        sh 'docker push lucky0524/spring-boot-mongo'
     }
     
}

