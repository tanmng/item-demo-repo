pipeline {
  agent any
  stages {
    stage ('test') {
      steps {
        echo "Hello, World"
      }
    }
    stage ('Build  Docker image') {
      steps {
        sh '''
            docker build --rm -t foobar .
        '''
      }
    }
    stage ('Login to ECR') {
      steps {
        sh '''
            $(aws ecr get-login --no-include-email --region us-east-1)
        '''
      }
    }
    stage ('Tag and push docker image') {
      steps {
        sh '''
            docker tag foobar 881926258290.dkr.ecr.us-east-1.amazonaws.com/tan-demo-hackathon:latest;
            docker push 881926258290.dkr.ecr.us-east-1.amazonaws.com/tan-demo-hackathon:latest;
        '''
      }
    }
  }
}
