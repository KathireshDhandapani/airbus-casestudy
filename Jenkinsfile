pipeline {
  agent any
  stages {
    stage('Prepare Calculation Service') {
      steps {
        dir(path: 'source/calculation-offer-service/CalculationServiceAPISolution') {
          sh 'pwd'
          sh 'docker build -t $CALCULATION_SERVICE_IMAGE:latest -t $CALCULATION_SERVICE_IMAGE:$BUILD_NUMBER .'
          sh 'docker tag $CALCULATION_SERVICE_IMAGE:latest $ECR_ID/$CALCULATION_SERVICE_IMAGE:latest'
          sh 'docker tag $CALCULATION_SERVICE_IMAGE:$BUILD_NUMBER $ECR_ID/$CALCULATION_SERVICE_IMAGE:$BUILD_NUMBER'
          sh 'docker login --username $ECR_CREDENTIALS_USR --password $ECR_CREDENTIALS_PSW $ECR_ID'
          sh 'docker image prune -f'
          sh 'docker push $ECR_ID/$CALCULATION_SERVICE_IMAGE:latest'
        }

      }
    }

  }
  environment {
    ECR_ID = '142198642907.dkr.ecr.ap-south-1.amazonaws.com'
    CALCULATION_SERVICE_IMAGE = 'ramkumarv2-casestudy-calculation-service'
    ECR_CREDENTIALS = credentials('ecr-credentials')
  }
}