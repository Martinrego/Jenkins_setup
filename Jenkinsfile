pipeline {
  agent any
  stages {
    stage('github') {
      steps {
        echo 'pull the github code'
      }
    }

    stage('smoke test') {
      parallel {
        stage('smoke test') {
          steps {
            echo 'smoke test needs to complete'
          }
        }

        stage('automation repo') {
          steps {
            git(url: 'https://github.com/Martinrego/EyeAutomation', branch: 'Master', poll: true)
          }
        }

        stage('Maven QA build') {
          steps {
            bat 'mvn test -DEnvironment=QAt'
          }
        }

      }
    }

    stage('certify') {
      steps {
        echo 'QA need to certify'
      }
    }

  }
}