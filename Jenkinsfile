pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'gradle build '
      }
    }

    stage('mail Notificatoin') {
      steps {
        mail(subject: 'Build succes', body: 'the buils on Matrix api is completed ', from: 'yaaacine@gmail.com', to: 'gy_zidelmal@esi.dz')
      }
    }

    stage('code review') {
      steps {
      
      }
    }

  }
}
