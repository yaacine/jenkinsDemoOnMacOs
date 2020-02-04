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

    stage('code Review') {
      parallel {
        stage('code Review') {
          steps {
            withSonarQubeEnv('sonar') {
              sh 'gradle sonarQube'
            }

          }
        }

        stage('test reporting') {
          steps {
            jacoco(buildOverBuild: true)
          }
        }

      }
    }

    stage('deployement') {
      when{
        branch 'master'
      }
      steps {
        sh 'gradle publish'
      }
    }

    stage('slack notification') {
       when{
        branch 'master'
      }
      steps {
        slackSend(token: 'TRT34LYF8/BSMC2FW23/buxcNiFEunZFTD46KGbj8gaA', baseUrl: 'https://hooks.slack.com/services/', teamDomain: 'https://esioutilsyacine.slack.com/', message: 'deployement done', channel: 'général')
      }
    }

  }
}
