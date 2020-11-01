pipeline {
  agent any
  stages {
    stage('Smoke Test') {
      steps {
        echo 'Smoke test is going to start'
        git(url: 'https://github.com/LeafPages/EyeAutomation', branch: 'master', poll: true)
        bat(script: 'mvn test -DEnvironment=QA', label: 'QA Smoke')
      }
    }

    stage('Sanity Test in QA') {
      steps {
        echo 'About to run Sanity in QA'
        bat(script: 'mvn test -DEnvironment=QA', label: 'Maven QA')
      }
    }

    stage('Ceritication') {
      steps {
        input(message: 'Manually do', ok: 'Yes')
        waitUntil()
      }
    }

  }
}