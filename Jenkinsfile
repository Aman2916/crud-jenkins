pipeline {
  agent any

  stages {
    stage('Install Dependencies') {
      steps {
        bat 'npm install'
      }
    }

    stage('Run Tests') {
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
