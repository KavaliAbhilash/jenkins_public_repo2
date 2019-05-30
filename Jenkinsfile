pipeline {
  agent any
  parameters {
        string(name: 'SVNCHKOUTURL', defaultValue: 'test', description: 'How should I greet the world?')
    }
  stages {
    stage('build') {
      steps {
        bat 'mvn --version'
      }
    }
    stage('Backend') {
      parallel {
        stage('perf') {
          steps {
            build job: 'TEST_JOB' , parameters:[ string(name: 'VALUE_NAME',value: SVNCHKOUTURL) ]
          }
        }
        stage('Unit') {
          steps {
            bat 'echo " Unit test"'
          }
        }
      }
    }
    stage('Frontend') {
      steps {
        bat 'echo "frontend"'
      }
    }
    stage('static code analsysis') {
      steps {
        sleep 5
      }
    }
    stage('Deploy') {
      steps {
        bat 'echo "deploy"'
      }
    }
  }
}
