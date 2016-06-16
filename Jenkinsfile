#!groovy

// NOTE: this is a generic Jenkinsfile, if we had a multibranch pipeline
// it would use this Jenkinsfile to run the pipeline...

node('master') {
  stage 'checkout'
  git branch: 'master', url: 'https://bitbucket.org/boise_devops_2016/hello.git'
  stage 'build'
  echo "build a simple job"
}

stage 'test - unit and static'
parallel (
  staticAnalysis: {
    node('master') {
        echo 'run static code analysis'
        sleep 5
    }
  },
  unitTesting: {
    node('master') {
        echo 'unit testing'
        sleep 10
    }
  }
)
