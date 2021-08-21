pipeline {

  agent {
    docker {
      image 'python:3.8-slim-buster'
      args '-u 0:0 -v /tmp/flask-docker:/root/.cache'
    }
  }

  environment {
    DOCKER_IMAGE = "hunghq1096/flask-docker"
  }

  stages {
    stage("Test1") {
      // agent {
      //     docker {
      //       image 'python:3.8-slim-buster'
      //       args '-u 0:0 -v /tmp/flask-docker:/root/.cache'
      //     }
      // }
      steps {
        echo "Test1"
        sh "pip install poetry"
        sh "poetry install"
        sh "poetry run pytest"
      }
    }

    stage("Test2") {
      // agent {
      //     docker {
      //       image 'python:3.8-slim-buster'
      //       args '-u 0:0 -v /tmp/flask-docker:/root/.cache'
      //     }
      // }
      steps {
        echo "Test2"
        sh "pip install poetry"
        sh "poetry install"
        sh "poetry run pytest"
      }
    }

    // stage("build") {
    //   agent { node {label 'master'}}
    //   environment {
    //     DOCKER_TAG="${GIT_BRANCH.tokenize('/').pop()}-${GIT_COMMIT.substring(0,7)}"
    //   }
    //   steps {
    //     sh "docker build -t ${DOCKER_IMAGE}:${DOCKER_TAG} . "
    //     sh "docker tag ${DOCKER_IMAGE}:${DOCKER_TAG} ${DOCKER_IMAGE}:latest"
    //     sh "docker image ls | grep ${DOCKER_IMAGE}"
    //     withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
    //         sh 'echo $DOCKER_PASSWORD | docker login --username $DOCKER_USERNAME --password-stdin'
    //         sh "docker push ${DOCKER_IMAGE}:${DOCKER_TAG}"
    //         sh "docker push ${DOCKER_IMAGE}:latest"
    //     }

    //     //clean to save disk
    //     sh "docker image rm ${DOCKER_IMAGE}:${DOCKER_TAG}"
    //     sh "docker image rm ${DOCKER_IMAGE}:latest"
    //   }
    // }
  }

  post {
    success {
      echo "SUCCESSFUL"
    }
    failure {
      echo "FAILED"
    }
  }
}
