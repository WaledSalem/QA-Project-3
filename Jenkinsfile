pipeline{
    agent any
    parameters {
        booleanParam (
            defaultValue: true,
            description: '',
            name: 'DEPLOY')
    }
    stages{       
        stage('Deploy'){
            when {
                expression { params.DEPLOY == true }
            }
            steps{
                sh label: '', script:
                '''
                #!/bin/bash
                ssh -i ~/.ssh/jenkins-key.pem ubuntu@ec2-13-49-241-40.eu-north-1.compute.amazonaws.com << EOF
                rm -rf QA-Project-3 
                git clone https://github.com/WaledSalem/QA-Project-3.git
                cd QA-Project-3
                git pull
                kubectl apply -f Kubernetes_manifests/
                sleep 10s
                kubectl get services
                '''
            }
        }
    }
}
