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
    stage('Authenticate'){
        
        bat ''' ibmcloud login --apikey Qq_u7Mtvj49InsKyzkFDipkQZxRUZMTEanGtRAOL3Ite -r  us-south -g Default
            ibmcloud plugin install -f container-service
            ibmcloud plugin install -f container-registry
            ibmcloud plugin install -f observe-service
            ibmcloud plugin list
            ibmcloud ks cluster config --cluster c0rj4r1d0huad5id0ut0
                    
             '''      
    }
    
    stage('Kubernetes pod'){
        bat "ibmcloud ks cluster config --cluster c0rj4r1d0huad5id0ut0"
        bat "kubectl config current-context"
        bat 'kubectl apply -f servicepy.yaml'
        bat 'kubectl apply -f flask-deployment.yaml'
        
        bat 'kubectl get pods'
    }
}
