pipeline {
  agent {
    docker {
      args '-p 5000:5000'
      image 'alpine'
    }

  }
  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        sh 'apk add --update alpine-sdk'
        sh 'apk add --update python3 py3-cffi py3-flask py3-jinja2 py3-markupsafe py3-lxml'
        sh 'python3 -m ensurepip'
        sh 'pip3 install -U pip'
        sh 'pip install -r requirements.txt'
        sh 'python3 ./netconf \\menu/main.py'
      }
    }

    stage('Test') {
      steps {
        echo 'Testing..'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying....'
      }
    }

  }
  environment {
    registry = ' malikmargaret/new'
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
}