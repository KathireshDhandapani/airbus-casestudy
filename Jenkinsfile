pipeline {
  agent any
  stages {
    stage('Prepare Calculation Service') {
      steps {
        dir(path: 'source/calculation-offer-service/CalculationServiceAPISolution') {
          sh 'pwd'
        }

      }
    }

  }
  environment {
    ECR_ID = '142198642907.dkr.ecr.ap-south-1.amazonaws.com'
    CALCULATION_SERVICE_IMAGE = 'ramkumarv2-casestudy-calculation-service'
  }
}