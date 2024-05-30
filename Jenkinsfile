node{
    stage('Git checkout'){
        git branch: 'main', url: 'https://github.com/eguniti/backend.git'
    }
    
    stage('Build Image and push to ECR'){
        sh 'cd /var/lib/jenkins/workspace/create_backend_image/'
        sh 'docker image build -t backend/$JOB_NAME:v1.$BUILD_NUMBER .'
        sh 'docker tag backend/$JOB_NAME:v1.$BUILD_NUMBER 730335564461.dkr.ecr.us-east-1.amazonaws.com/backend:v1.$BUILD_NUMBER'
        sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 730335564461.dkr.ecr.us-east-1.amazonaws.com'
        sh 'docker push 730335564461.dkr.ecr.us-east-1.amazonaws.com/backend:v1.$BUILD_NUMBER'
    }
}
