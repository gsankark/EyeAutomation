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

    stage('Ceritication') {
      when {
        branch 'master'
      }
      steps {
        echo 'QA Certified'
      }
    }

  }
}