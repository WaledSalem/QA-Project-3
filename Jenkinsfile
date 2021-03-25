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
                chmod 400 /home/ubuntu/.ssh/kube-key.pem
                ssh -i /home/ubuntu/.ssh/kube-key.pem ubuntu@ec2-13-53-168-103.eu-north-1.compute.amazonaws.com << EOF
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
