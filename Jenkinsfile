pipeline {
  agent any

  environment {
    MONGO_URL = credentials('MONGO_URL')
    PORT = '3000'
  }

  stages {
    stage('Install') {
      steps {
        bat 'npm install'
      }
    }

    stage('Test') {
      steps {
        bat 'npm test'
      }
    }

    stage('Deploy') {
      steps {
        bat '''
          pm2 restart crud-app || pm2 start app.js --name crud-app
        '''
      }
    }
  }
}
