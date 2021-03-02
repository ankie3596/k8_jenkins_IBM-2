node {
    stage('Get Source'){
        git 'https://github.com/ankie3596/k8_jenkins_IBM-2.git'
        
    }
    stage('Docker-build'){
        sh 'docker build -t ankimittal/k8-1 .'
    }
    stage('Docker-push'){
        docker.withRegistry('https://registry.hub.docker.com','Docker'){
            def customImage = docker.build('ankimittal/k8-1')
            customImage.push()
        }
    }
    stage('Kubernetes pod'){
        sh 'kubectl apply -f servicepy.yaml'
        sh 'kubectl apply -f flask-deployment.yaml'
        sh 'kubectl get pods'
    }
}
