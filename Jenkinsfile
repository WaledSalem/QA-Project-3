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
                ssh -i ~/.ssh/jenkins-key.pem ubuntu@13.48.100.188 << EOF
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
