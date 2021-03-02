node {
    stage('Get Source'){
        git 'https://github.com/ankie3596/k8_jenkins_IBM-2.git'
        
    }
   
    stage('Docker-push'){
        docker.withRegistry('https://registry.hub.docker.com','DockerId'){
            def customImage = docker.build('ankimittal/k8-1')
            customImage.push()
        }
    }
    stage('Kubernetes pod'){
        bat 'kubectl apply -f servicepy.yaml'
        bat 'kubectl apply -f flask-deployment.yaml'
        bat 'kubectl get pods'
    }
}
